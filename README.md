# avd2
<img width="778" height="508" alt="image" src="https://github.com/user-attachments/assets/a169b052-2ffa-4ce9-830a-eea8acea5b09" />

```
# Monte Carlo odhad π
N <- 100000
x <- runif(N, -1, 1)
y <- runif(N, -1, 1)
inside <- (x^2 + y^2) <= 1
pi_hat <- 4 * mean(inside)
pi_hat

```

<img width="820" height="625" alt="image" src="https://github.com/user-attachments/assets/2d6b823b-05d5-4d46-a5ca-f5c9818ceb1a" />

```
# Přechodová matice (2 stavy: zákazník kupuje A nebo B)
P <- matrix(c(0.7, 0.3,
              0.4, 0.6), nrow=2, byrow=TRUE)

# počáteční rozdělení (všichni začínají u A)
pi <- c(1,0)

# simulace 10 kroků
for (t in 1:10) {
  pi <- pi %*% P
  print(pi)
}

```

<img width="820" height="881" alt="image" src="https://github.com/user-attachments/assets/6f7f9ea0-6218-418d-8dfc-fb8e29b2eba3" />

```
library(markovchain)

states <- c("Email","Social","Web","Buy")
trans <- matrix(c(
  0.1,0.4,0.4,0.1,
  0.2,0.2,0.5,0.1,
  0.1,0.1,0.6,0.2,
  0,0,0,1), nrow=4, byrow=TRUE)

mc <- new("markovchain", states=states, transitionMatrix=trans)
steadyStates(mc)  # dlouhodobá pravděpodobnost

```

```
P <- matrix(c(0.9, 0.1, 0.0,
              0.0, 0.0, 1.0,
              0.8, 0.2, 0.0), nrow=3, byrow=TRUE)
states <- c("Funkční","Porucha","Oprava")
mc <- new("markovchain", states=states, transitionMatrix=P)
steadyStates(mc)

```
<img width="758" height="967" alt="image" src="https://github.com/user-attachments/assets/cc86b0c2-ba4f-4f9f-916b-89bdea957dfd" />

```
# Parametry EOQ
D <- 10000  # poptávka
S <- 50     # náklady na objednávku
H <- 2      # náklady na skladování

Q_opt <- sqrt((2*D*S)/H)
Q_opt
---------
set.seed(123)
T <- 30   # počet dní
demand <- rpois(T, lambda=20)  # náhodná denní poptávka
stock <- rep(0,T)
stock[1] <- 100

for (t in 2:T) {
  stock[t] <- stock[t-1] - demand[t-1]
  if (stock[t] < 30) stock[t] <- stock[t] + 100  # doplnění zásob
}
plot(stock, type="o", main="Simulace zásob")

```

<img width="814" height="394" alt="image" src="https://github.com/user-attachments/assets/d004f12f-7005-4c79-b8b3-fb238f466a78" />

```
library(queueing)

input <- NewInput.MM1(lambda=0.8, mu=1) # λ=0.8 příchody, μ=1 obsluha
model <- QueueingModel(input)
summary(model)

```
