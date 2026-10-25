# Virtual-Wallet

Virtual Wallet – Sports Wager Prediction is a standalone Java desktop application.

**The problem it addresses**

The application provides a controlled environment where users can manage virtual funds and predict the outcomes of sports matches. It tracks the money used for bets, records predictions, and updates balances when results are declared. 

A traditional wallet application mainly handles deposits, withdrawals, and transaction history. Our project extends that idea by introducing a match-prediction and settlement workflow.

**End-to-end workflow**

1.	Register an admin account. Registration validates that username is not blank, password is at least four characters, and username is not already used.
2.	The application hashes the password using BCrypt and stores a user record. It creates a wallet account for that user.
3.	The admin creates a match by entering the home team, away team, and three outcome probabilities.
4.	OddsService normalizes the probabilities and calculates decimal odds with the default 5% margin.
5.	The player registers a separate PLAYER account, tops up the wallet, selects an open match and outcome, enters a stake, and places a bet.
6.	BettingService checks the stake, match status, wallet balance and outcome selection. It deducts the stake, records a ledger entry, and inserts the bet in one transaction.
7.	The admin declares the match result. SettlementService processes open bets: matching picks win and receive a payout; other picks lose.
8.	The player logs back in and sees the updated wallet balance and bet status.

**Technologies used**

Java 21, JavaFX, Maven, H2 Database, JDBC, SQL, BCrypt, BigDecimal, JUnit5

## Run it
```bash
cd virtual-wallet
mvn clean javafx:run
```

## Run the tests
```bash
mvn test
```

## Try it out
1. Launch the app, click **Register**, create an account with role **ADMIN**.
2. You'll land on the Admin screen. Create a match, e.g. "Arsenal" vs
   "Liverpool" with probabilities `0.45`, `0.25`, `0.30` (home/draw/away).
   The app turns these into odds automatically.
3. Log out, register a second account with role **PLAYER**.
4. Top up your wallet, select the match, pick HOME/DRAW/AWAY, enter a
   stake, and place the bet.
5. Log back in as the admin, select the match, choose the result, and
   click **Settle Selected Match**. Log back in as the player to see the
   bet marked WON or LOST and the wallet balance updated.
