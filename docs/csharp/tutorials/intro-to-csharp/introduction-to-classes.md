---
title: Klasy i obiekty — wprowadzenie do samouczka języka C#
description: Tworzenie pierwszego programu C# i eksplorowanie koncepcji obiektowych
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: b6ad72997647b80b981f1a1871e384791404bdf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156596"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Eksplorowanie programowania obiektowego za pomocą klas i obiektów

Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia. Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS. Szybki przegląd poleceń, których będziesz używać, znajduje się w [obszarze Zaznajomij się z narzędziami programistycznymi](local-environment.md) z łączami do szczegółowych informacji.

## <a name="create-your-application"></a>Tworzenie aplikacji

Korzystając z okna terminala, utwórz katalog o nazwie *klasy*. Stworzysz tam aplikację. Zmień ten katalog `dotnet new console` i wpisz w oknie konsoli. To polecenie tworzy aplikację. Otwórz *Program.cs*. Powinny wyglądać następująco:

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

W tym samouczku masz zamiar utworzyć nowe typy, które reprezentują konto bankowe. Zazwyczaj deweloperzy definiują każdą klasę w innym pliku tekstowym. To sprawia, że łatwiej zarządzać w miarę wzrostu rozmiaru programu. Utwórz nowy plik o nazwie *BankAccount.cs* w katalogu *klas.*

Ten plik będzie zawierał definicję ***konta bankowego***. Programowanie obiektowe organizuje kod, tworząc typy w postaci ***klas***. Klasy te zawierają kod, który reprezentuje określoną jednostkę. Klasa `BankAccount` reprezentuje konto bankowe. Kod implementuje określone operacje za pomocą metod i właściwości. W tym samouczku konto bankowe obsługuje to zachowanie:

1. Posiada 10-cyfrowy numer, który jednoznacznie identyfikuje konto bankowe.
1. Ma ciąg, który przechowuje nazwę lub nazwy właścicieli.
1. Saldo można pobrać.
1. Przyjmuje depozyty.
1. Akceptuje wypłaty.
1. Saldo początkowe musi być dodatnie.
1. Wypłaty nie mogą skutkować ujemnym saldem.

## <a name="define-the-bank-account-type"></a>Definiowanie typu konta bankowego

Można rozpocząć od utworzenia podstaw klasy, która definiuje to zachowanie. Wyglądałoby to tak:

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

Zanim przejdziesz dalej, przyjrzyjmy się temu, co zbudowałeś.  Deklaracja `namespace` zapewnia sposób logicznie zorganizować kod. Ten samouczek jest stosunkowo mały, więc umieścisz cały kod w jednej przestrzeni nazw.

`public class BankAccount`definiuje klasę lub typ, który tworzysz. Wszystko wewnątrz `{` `}` i że następuje deklaracja klasy definiuje stan i zachowanie klasy. Istnieje pięciu ***członków*** `BankAccount` klasy. Pierwsze trzy to ***właściwości***. Właściwości są elementami danych i może mieć kod, który wymusza sprawdzanie poprawności lub inne reguły. Ostatnie dwie to ***metody***. Metody są bloki kodu, które wykonują jedną funkcję. Czytanie nazw każdego z członków należy podać wystarczającą ilość informacji dla Ciebie lub innego dewelopera, aby zrozumieć, co robi klasa.

## <a name="open-a-new-account"></a>Otwieranie nowego konta

Pierwszą funkcją do wdrożenia jest otwarcie konta bankowego. Gdy klient otwiera konto, musi podać początkowe saldo i informacje o właścicielu lub właścicielach tego konta.

Tworzenie nowego obiektu `BankAccount` typu oznacza definiowanie ***konstruktora,*** który przypisuje te wartości. ***Konstruktor*** jest elementem członkowskim, który ma taką samą nazwę jak klasa. Służy do inicjowania obiektów tego typu klasy. Dodaj następujący konstruktor do `BankAccount` typu:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory są wywoływane podczas [`new`](../../language-reference/operators/new-operator.md)tworzenia obiektu przy użyciu . Zastąp wiersz `Console.WriteLine("Hello World!");` w *Program.cs* `<name>` na następujący kod (zamień na swoje imię i nazwisko):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Wpisz, `dotnet run` aby zobaczyć, co się dzieje.  

Czy zauważyłeś, że numer konta jest pusty? Nadszedł czas, aby to naprawić. Numer konta powinien być przypisany, gdy obiekt jest skonstruowany. Ale nie powinno być obowiązkiem dzwoniącego, aby go utworzyć. Kod `BankAccount` klasy powinien wiedzieć, jak przypisać nowe numery kont.  Prostym sposobem na to jest zacząć od numeru 10-cyfrowego. Zwiększaj go podczas tworzenia każdego nowego konta. Na koniec przechowuj numer bieżącego konta, gdy obiekt jest konstruowany.

Dodaj następującą deklarację `BankAccount` elementu członkowskiego do klasy:

```csharp
private static int accountNumberSeed = 1234567890;
```

Jest to element członkowski danych. Jest `private`, co oznacza, że jest dostępny tylko `BankAccount` przez kod wewnątrz klasy. Jest to sposób oddzielenia obowiązków publicznych (np. posiadania numeru konta) od implementacji prywatnej (sposób generowania numerów kont). Jest to `static`również , co oznacza, `BankAccount` że jest współużytkowany przez wszystkie obiekty. Wartość zmiennej niestatycznej jest unikatowa `BankAccount` dla każdego wystąpienia obiektu. Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Wpisz, `dotnet run` aby wyświetlić wyniki.

## <a name="create-deposits-and-withdrawals"></a>Tworzenie wpłat i wypłat

Twoja klasa konta bankowego musi akceptować wpłaty i wypłaty, aby działały poprawnie. Zaimplementujmy wpłaty i wypłaty, tworząc arkusz każdej transakcji dla konta. To ma kilka zalet w porównaniu z po prostu aktualizacją salda każdej transakcji. Historia może służyć do inspekcji wszystkich transakcji i zarządzania dziennymi saldami. Obliczając saldo z historii wszystkich transakcji w razie potrzeby, wszelkie błędy w pojedynczej transakcji, które są stałe zostaną poprawnie odzwierciedlone w saldzie przy następnym obliczeniu.

Zacznijmy od utworzenia nowego typu do reprezentowania transakcji. Jest to prosty typ, który nie ma żadnych obowiązków. Potrzebuje kilku właściwości. Utwórz nowy plik o nazwie *Transaction.cs*. Dodaj do niej następujący kod:

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

Teraz dodajmy <xref:System.Collections.Generic.List%601> obiekty `Transaction` do `BankAccount` klasy. Dodaj następującą deklarację:

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

Klasa <xref:System.Collections.Generic.List%601> wymaga zaimportowania innego obszaru nazw. Na początku *BankAccount.cs*dodaj następujące elementy:

```csharp
using System.Collections.Generic;
```

Teraz zmieńmy sposób zgłaszania. `Balance`  Można go znaleźć, sumując wartości wszystkich transakcji. Zmodyfikuj `Balance` `BankAccount` deklarację w klasie na:

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

W tym przykładzie przedstawiono ważny aspekt ***właściwości***. Teraz obliczasz równowagę, gdy inny programista prosi o wartość. Obliczenia wyliczają wszystkie transakcje i zawiera sumę jako bieżące saldo.

Następnie zaimplementuj `MakeDeposit` i `MakeWithdrawal` metody. Metody te będą wymuszać dwie ostatnie zasady: że początkowe saldo musi być dodatnie i że każde wycofanie nie może stworzyć ujemnego salda.

Wprowadza to pojęcie ***wyjątków***. Standardowy sposób wskazujący, że metoda nie może ukończyć pomyślnie swojej pracy jest zgłosić wyjątek. Typ wyjątku i skojarzony z nim komunikat opisują błąd. W tym `MakeDeposit` miejscu metoda zgłasza wyjątek, jeśli kwota depozytu jest ujemna. Metoda `MakeWithdrawal` zgłasza wyjątek, jeśli kwota wypłaty jest ujemna lub jeśli zastosowanie wypłaty powoduje ujemne saldo:

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

Instrukcja [`throw`](../../language-reference/keywords/throw.md) **zgłasza** wyjątek. Wykonywanie bieżącego bloku kończy się i kontroli `catch` transferów do pierwszego pasującego bloku znaleźć w stosie wywołań. Dodasz blok, `catch` aby przetestować ten kod nieco później.

Konstruktor powinien uzyskać jedną zmianę, tak aby dodaje transakcję początkową, a nie bezpośrednio aktualizować saldo. Ponieważ metoda została `MakeDeposit` już zapisano, wywołaj ją z konstruktora. Gotowy konstruktor powinien wyglądać tak:

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<xref:System.DateTime.Now?displayProperty=nameWithType>jest właściwością, która zwraca bieżącą datę i godzinę. Przetestuj to, dodając kilka wpłat i wypłat w swojej `Main` metodzie:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

Następnie sprawdź, czy są przechwytywanie warunków błędu, próbując utworzyć konto z ujemnym saldem:

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

Użyj [ `try` `catch` i instrukcje,](../../language-reference/keywords/try-catch.md) aby oznaczyć blok kodu, który może zgłaszać wyjątki i przechwycić te błędy, które można oczekiwać. Tej samej techniki można użyć do testowania kodu, który zgłasza wyjątek dla ujemnego salda:

```csharp
// Test for a negative balance.
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

Zapisz plik i `dotnet run` wpisz, aby go wypróbować.

## <a name="challenge---log-all-transactions"></a>Wyzwanie - rejestruj wszystkie transakcje

Aby zakończyć ten samouczek, można napisać `GetAccountHistory` metodę, która tworzy `string` dla historii transakcji. Dodaj tę metodę `BankAccount` do typu:

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

Używa <xref:System.Text.StringBuilder> klasy do formatowania ciągu, który zawiera jeden wiersz dla każdej transakcji. Widzieliście kod formatowania ciągu wcześniej w tych samouczkach. Jedną z `\t`nowych postaci jest . Wstawia kartę, aby sformatować dane wyjściowe.

Dodaj ten wiersz, aby przetestować go w *Program.cs:*

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Wpisz, `dotnet run` aby wyświetlić wyniki.

## <a name="next-steps"></a>Następne kroki

Jeśli utknąłeś, możesz zobaczyć źródło tego samouczka [w naszym reppo GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).

Gratulacje, zakończyłeś wszystkie nasze wprowadzenie do samouczków języka C#. Jeśli chcesz dowiedzieć się więcej, spróbuj więcej naszych [tutoriali](../index.md).
