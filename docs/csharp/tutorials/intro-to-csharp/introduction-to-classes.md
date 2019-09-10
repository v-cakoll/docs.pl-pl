---
title: Klasy i obiekty — wprowadzenie do C# samouczka
description: Utwórz pierwszy C# program i Eksploruj koncepcje zorientowane obiektowo
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 092639e86b3e8e683a7d5f6ecf5b732991581b71
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850735"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Eksploruj programowanie zorientowane obiektowo przy użyciu klas i obiektów

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego na komputerach Mac, komputerze lub Linux. Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.

## <a name="create-your-application"></a>Tworzenie aplikacji

Za pomocą okna terminalu Utwórz katalog o nazwie **Classes**. W tym miejscu utworzysz aplikację. Przejdź do tego katalogu i wpisz `dotnet new console` w oknie konsoli. To polecenie tworzy aplikację. Otwórz **program.cs**. Powinny wyglądać następująco:

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

W tym samouczku utworzysz nowe typy reprezentujące konto bankowe. Zazwyczaj deweloperzy definiują każdą klasę w innym pliku tekstowym. Ułatwia to zarządzanie w miarę zwiększania się rozmiaru programu.  Utwórz nowy plik o nazwie **BankAccount.cs** w katalogu **Classes** . 

Ten plik będzie zawierać definicję ***konta bankowego***. Programowanie zorientowane obiektowo organizuje kod przez tworzenie typów w postaci ***klas***. Klasy te zawierają kod, który reprezentuje konkretną jednostkę. `BankAccount` Klasa reprezentuje konto bankowe. Kod implementuje określone operacje za pomocą metod i właściwości. W tym samouczku konto bankowe obsługuje takie zachowanie:

1. Ma 10-cyfrowy numer, który jednoznacznie identyfikuje konto bankowe.
1. Zawiera on ciąg przechowujący nazwę lub nazwy właścicieli.
1. Można pobrać saldo.
1. Akceptuje ona depozyty.
1. Akceptuje on wycofania.
1. Saldo początkowe musi mieć wartość dodatnią.
1. Wycofanie nie może spowodować negatywnego salda.

## <a name="define-the-bank-account-type"></a>Definiowanie typu konta bankowego

Można rozpocząć od utworzenia podstawowych podstaw klasy, które definiują takie zachowanie. Będzie to wyglądać następująco:

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

Przed rozpoczęciem przejdźmy do tego, co zostało skompilowane.  `namespace` Deklaracja umożliwia logicznie organizowanie kodu. Ten samouczek jest stosunkowo mały, więc umieścisz cały kod w jednej przestrzeni nazw. 

`public class BankAccount`definiuje klasę lub typ, który tworzysz. Wszystko wewnątrz `{` i `}` , które następuje po deklaracji klasy, definiuje zachowanie klasy. Istnieje pięć ***członków*** `BankAccount` klasy. Pierwsze trzy są ***właściwościami***. Właściwości są elementami danych i mogą mieć kod, który wymusza walidację lub inne reguły. Ostatnie dwa są ***metodami***. Metody to bloki kodu, które wykonują pojedynczą funkcję. Odczytywanie nazw każdego z członków powinno zapewnić wystarczającą ilość informacji dla Ciebie lub innego dewelopera, aby zrozumieć, co robi Klasa.

## <a name="open-a-new-account"></a>Otwórz nowe konto

Pierwsza funkcja do wdrożenia polega na otwarciu konta bankowego. Gdy klient otworzy konto, musi podać początkowe saldo i informacje o właścicielu lub właściciele tego konta. 

Tworzenie nowego obiektu `BankAccount` typu oznacza zdefiniowanie ***konstruktora*** , który przypisuje te wartości. ***Konstruktor*** jest członkiem, który ma taką samą nazwę jak Klasa. Służy do inicjowania obiektów tego typu klasy. Dodaj następujący Konstruktor do `BankAccount` typu:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory są wywoływane podczas tworzenia obiektu za pomocą [`new`](../../language-reference/operators/new-operator.md). Zastąp wiersz `Console.WriteLine("Hello World!");` w ***program.cs*** następującym wierszem (Zastąp `<name>` nazwą):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Wpisz `dotnet run` , aby zobaczyć, co się dzieje.  

Czy na pewno numer konta jest pusty? Czas na rozwiązanie tego problemu. Numer konta powinien być przypisany podczas konstruowania obiektu. Ale nie powinien być odpowiedzialny za utworzenie go przez obiekt wywołujący. Kod `BankAccount` klasy powinien wiedzieć, jak przypisać nowe numery kont.  Prostym sposobem, aby to zrobić, jest rozpoczęcie z 10-cyfrową liczbą. Zwiększ ją po utworzeniu każdego nowego konta. Na koniec Zapisz bieżący numer konta w przypadku konstruowania obiektu.

Dodaj następującą deklarację elementu członkowskiego `BankAccount` do klasy:

```csharp
private static int accountNumberSeed = 1234567890;
```

To jest element członkowski danych. Oznacza to `BankAccount` , że można uzyskać do niego dostęp tylko przez kod wewnątrz klasy. `private` Jest to sposób oddzielenia publicznych obowiązków (na przykład numeru konta) od implementacji prywatnej (jak są generowane numery kont). Jest to również `static`, co oznacza, że jest ono współużytkowane `BankAccount` przez wszystkie obiekty. Wartość zmiennej niestatycznej jest unikatowa dla każdego wystąpienia `BankAccount` obiektu. Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Wpisz `dotnet run` , aby wyświetlić wyniki.

## <a name="create-deposits-and-withdrawals"></a>Utwórz depozyty i Wycofaj

Twoja Klasa konta bankowego musi akceptować depozyty i wycofywania, aby działały prawidłowo. Zaimplementujmy depozyty i wycofania, tworząc arkusz każdej transakcji dla konta. Ma kilka korzyści w porównaniu do zwykłego aktualizowania salda każdej transakcji. Historia może służyć do inspekcji wszystkich transakcji i zarządzania bilansami dziennymi. Dzięki wykorzystaniu salda z historii wszystkich transakcji, gdy jest to potrzebne, wszelkie błędy w pojedynczej transakcji, które są stałe, zostaną prawidłowo odzwierciedlone w saldzie następnego obliczenia.

Zacznijmy od utworzenia nowego typu do reprezentowania transakcji. Jest to prosty typ, który nie ma żadnych obowiązków. Potrzebuje on kilku właściwości. Utwórz nowy plik o nazwie ***Transaction.cs***. Dodaj do niego następujący kod:

[!code-csharp[Transaction](../../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Teraz Dodajmy <xref:System.Collections.Generic.List%601> `Transaction` obiekty do `BankAccount` klasy. Dodaj następującą deklarację:

[!code-csharp[TransactionDecl](../../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601> Klasa wymaga zaimportowania innej przestrzeni nazw. Dodaj następujące elementy na początku **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

Teraz Zmieńmy sposób `Balance` zgłaszania raportu.  Można go znaleźć, sumując wartości wszystkich transakcji. Zmodyfikuj deklarację `Balance` `BankAccount` klasy w klasie w następujący sposób:

[!code-csharp[BalanceComputation](../../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Ten przykład pokazuje istotny aspekt ***Właściwości***. Teraz trwa obliczanie salda, gdy inny programista pyta o wartość. Wyliczenie wylicza wszystkie transakcje i zawiera sumę jako bieżące saldo.

Następnie Zaimplementuj `MakeDeposit` metody i `MakeWithdrawal` . Te metody wymuszą dwie ostatnie reguły: początkowe saldo musi być dodatnie i że każde wycofanie nie może utworzyć salda ujemnego. 

Wprowadza to koncepcję ***wyjątków***. Standardowy sposób wskazujący, że metoda nie może zakończyć pracy, to zgłosić wyjątek. Typ wyjątku i komunikat skojarzony z nim opisują błąd. W `MakeDeposit` tym miejscu Metoda zgłasza wyjątek, jeśli kwota depozytu jest ujemna. `MakeWithdrawal` Metoda zgłasza wyjątek, jeśli kwota wycofania jest ujemna lub jeśli zastosowanie wycofania powoduje ujemne saldo:

[!code-csharp[DepositAndWithdrawal](../../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

Instrukcja zgłasza wyjątek. [`throw`](../../language-reference/keywords/throw.md) Wykonanie bieżącego bloku i sterowanie transferami do pierwszego zgodnego `catch` bloku znalezionego w stosie wywołań. Dodasz `catch` blok, aby przetestować ten kod nieco później.

Konstruktor powinien otrzymać jedną zmianę, aby dodać początkową transakcję zamiast bezpośrednio aktualizować saldo. Ponieważ już zapisano `MakeDeposit` metodę, wywołaj ją z konstruktora. Gotowy Konstruktor powinien wyglądać następująco:

[!code-csharp[Constructor](../../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType>jest właściwością zwracającą bieżącą datę i godzinę. Przetestuj to poprzez dodanie kilku depozytów i wycofaeń `Main` w ramach metody:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

Następnie należy sprawdzić, czy są przechwytywane warunki błędów, próbując utworzyć konto z ujemną wartością:

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

Za pomocą [ `try` instrukcji i `catch` ](../../language-reference/keywords/try-catch.md) można oznaczyć blok kodu, który może generować wyjątki i przechwytywać te błędy, których oczekujesz. Możesz użyć tej samej techniki, aby przetestować kod, który zgłasza wyjątek dla nieujemnego salda:

```csharp
// Test for a negative balance:
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

Zapisz plik i wpisz `dotnet run` , aby go wypróbować.

## <a name="challenge---log-all-transactions"></a>Wyzwanie — Rejestruj wszystkie transakcje

Aby ukończyć ten samouczek, można napisać `GetAccountHistory` metodę, która `string` tworzy dla historii transakcji. Dodaj tę metodę do `BankAccount` typu:

[!code-csharp[History](../../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Używa <xref:System.Text.StringBuilder> klasy do formatowania ciągu, który zawiera jeden wiersz dla każdej transakcji. W tych samouczkach pojawił się kod formatowania ciągu. Jeden nowy znak to `\t`. Spowoduje to wstawienie karty w celu sformatowania danych wyjściowych.

Dodaj ten wiersz, aby przetestować go w **program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Wpisz `dotnet run` , aby wyświetlić wyniki.

## <a name="next-steps"></a>Następne kroki

Jeśli zawiesz, że możesz zobaczyć źródło tego samouczka [w naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)

Gratulacje, udało Ci się ukończyć wszystkie nasze wprowadzenie C# do samouczków. Jeśli eager chcesz dowiedzieć się więcej, wypróbuj więcej naszych [samouczków](../index.md)
