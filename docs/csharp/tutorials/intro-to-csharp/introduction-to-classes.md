---
title: Klasy i obiekty — wprowadzenie do C# samouczek
description: Tworzenie pierwszego programu C# i Eksploruj pojęcia zorientowana obiektowo
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 8b823e05ea5e51bb3096d6a0611630c996f56b33
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205376"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Zapoznaj się z zorientowana obiektowo Programowanie przy użyciu klas i obiektów

W tym samouczku oczekuje, że masz maszyny, których można użyć do tworzenia aplikacji. Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux. Krótkie omówienie poleceń użyjesz znajduje się w [zapoznanie się z narzędziami programistycznymi](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.

## <a name="create-your-application"></a>Tworzenie aplikacji

Za pomocą okna terminalu Utwórz katalog o nazwie **klasy**. Skompiluj aplikację istnieje. Przejdź do tego katalogu i wpisz `dotnet new console` w oknie konsoli. To polecenie umożliwia utworzenie aplikacji. Otwórz **Program.cs**. Jego powinien wyglądać następująco:

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

W ramach tego samouczka możesz zacząć tworzyć nowe typy, które reprezentują konto. Zwykle deweloperzy określają każdej klasy w pliku tekstowym różne. Ułatwia zarządzanie wzrostem program rozmiaru.  Utwórz nowy plik o nazwie **BankAccount.cs** w **klasy** katalogu. 

Ten plik będzie zawierać definicję ***konta bankowego***. Obiekt programowania Oriented organizuje kodu, tworząc typów w formie ***klasy***. Te klasy zawierają kod, który reprezentuje określonej jednostki. `BankAccount` Klasa reprezentuje konto. Kod implementuje określonych operacji w ramach metod i właściwości. W tym samouczku konta bankowego obsługuje to zachowanie:

1. Posiada 10-cyfrowy numer, który unikatowo identyfikuje koncie bankowym.
1. Ciąg, który przechowuje nazwę lub nazwy właścicieli w nim.
1. Mogą być pobierane równowagi.
1. Akceptuje depozyty.
1. Akceptuje wycofywania.
1. Saldo początkowe musi być dodatnia.
1. Wycofanie nie może być ujemna równowagi.

## <a name="define-the-bank-account-type"></a>Definiowanie typu konta bankowego

Możesz rozpocząć od utworzenia podstawy klasy, która definiuje to zachowanie. Wyglądałby następująco:

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

Przed przejściem, Spójrzmy na wcześniej skompilowana.  `namespace` Deklaracja umożliwia organizację kodu. Niniejszy samouczek jest stosunkowo mały, aby cały kod zostanie umieszczony w jednym obszarze nazw. 

`public class BankAccount` definiuje klasę lub typ tworzenia. Wszystko wewnątrz `{` i `}` następujący klasy deklaracja określa zachowanie klasy. Istnieje pięć ***członków*** z `BankAccount` klasy. Pierwsze trzy są ***właściwości***. Właściwości elementów danych i może mieć kod, który wymusza sprawdzania poprawności lub inne zasady. Ostatnie dwa są ***metody***. Metody to bloki kodu, które wykonują pojedynczą funkcję. Odczytywanie nazwy każdego z członków powinien zapewnić odpowiednią ilość informacji w lub innemu deweloperowi, aby zrozumieć działanie klasy.

## <a name="open-a-new-account"></a>Otwórz nowe konto

Pierwszą funkcją do zaimplementowania jest aby otworzyć konto. Gdy klient otworzy konto, musisz podać początkowego salda i informacji o właściciela lub właścicieli tego konta. 

Tworzenie nowego obiektu `BankAccount` typu polega na zdefiniowaniu ***Konstruktor*** , przypisuje tych wartości. A ***Konstruktor*** jest elementem członkowskim, który ma taką samą nazwę jak klasa. Służy do inicjowania obiektów tego typu klasy. Dodaj następującego konstruktora do `BankAccount` typu:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory są wywoływane podczas tworzenia obiektu przy użyciu [ `new` ](../../language-reference/keywords/new.md). Zastąp wiersz `Console.WriteLine("Hello World!");` w ***program.cs*** o następujący wiersz (Zastąp `<name>` z Twoją nazwą):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Typ `dotnet run` aby zobaczyć, co się dzieje.  

Zwróć uwagę, że numer konta jest puste? Nadszedł czas, aby rozwiązać ten problem. Powinien zostać przypisany numer konta, gdy obiekt jest konstruowany. Ale nie powinny być odpowiedzialność obiekt wywołujący, aby go utworzyć. `BankAccount` Kod klasy wiedzieć, jak przypisać nowy numery kont.  Najprościej można to zrobić, jest zaczynać się cyfrą 10 cyfr. Zwiększyć jej, po utworzeniu każdego nowego konta. Na koniec należy zapisać numer bieżącego konta, gdy obiekt jest konstruowany.

Dodaj następującą deklarację elementu członkowskiego do `BankAccount` klasy:

```csharp
private static int accountNumberSeed = 1234567890;
```

Jest to element członkowski danych. Ma ona `private`, co oznacza, że może zostać oceniony jedynie przez kod wewnątrz `BankAccount` klasy. Jest to sposób rozdzielania obowiązków publiczny (takie jak obsługa numer konta) z prywatnej implementacji (jak numery kont są generowane.) Warto również `static`, co oznacza, że jest współużytkowana przez wszystkie ``BankAccount`` obiektów. Wartość zmiennej niestatycznych jest unikatowy dla każdego wystąpienia ``BankAccount`` obiektu. Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Typ `dotnet run` aby zobaczyć wyniki.

## <a name="create-deposits-and-withdrawals"></a>Utwórz wpłat i wycofanie

Klasa konta bankowego musi zaakceptować wpłat i wycofania do prawidłowego działania. Umożliwia Implementowanie wpłat i wycofanie, tworząc dziennik każdej transakcji dla konta. Który ma kilka zalet w stosunku do zaktualizowania saldu każdej transakcji. Można historię inspekcji wszystkich transakcji i zarządzanie nimi salda dzienne. Za obliczenia równowagi z historii wszystkich transakcji, gdy potrzebne, wszelkie błędy w ramach jednej transakcji, które zostały usunięte zostaną prawidłowo odzwierciedlone w równowagi na następny obliczeń.

Zacznijmy od utworzenia nowego typu do reprezentowania transakcji. Jest to prosty typ, który nie ma żadnych obowiązki. Musi ona kilka właściwości. Utwórz nowy plik o nazwie ***Transaction.cs***. Dodaj następujący kod do niego:

[!code-csharp[Transaction](../../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Teraz Dodajmy <xref:System.Collections.Generic.List%601> z `Transaction` obiekty do `BankAccount` klasy. Dodaj następującą deklarację:

[!code-csharp[TransactionDecl](../../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601> Klasy, musisz zaimportować innej przestrzeni nazw. Dodaj następujący kod na początku **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

Teraz zmienimy sposób, w jaki `Balance` są zgłaszane.  Można je znaleźć przez zsumowanie wartości wszystkich transakcji. Zmodyfikuj deklarację zmiennej `Balance` w `BankAccount` klasy do następującego:

[!code-csharp[BalanceComputation](../../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

W tym przykładzie przedstawiono istotnym elementem ***właściwości***. Saldo jest teraz obliczeń, gdy programista innego poprosi o podanie wartości. Twoje obliczeń wylicza wszystkie transakcje oraz zapewnia Suma jako bieżące saldo.

Następnie należy zaimplementować `MakeDeposit` i `MakeWithdrawal` metody. Tych metod będzie wymuszać końcowego dwie reguły: czy saldo początkowe musi być liczbą dodatnią, a każde wystąpienie nie mogą tworzyć saldo ujemne. 

Wprowadza pojęcia ***wyjątki***. Standardowy sposób wskazujący, że metody nie może ukończyć swojej pracy pomyślnie jest zgłoszenie wyjątku. Typ wyjątku i komunikat skojarzony z nim opisuje błąd. W tym miejscu `MakeDeposit` metoda zgłasza wyjątek, jeśli ilość złożenia jest ujemna. `MakeWithdrawal` Metoda zgłasza wyjątek, jeśli kwota wycofania jest ujemna, czy stosowanie wycofanie skutkuje ujemne saldo:

[!code-csharp[DepositAndWithdrawal](../../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

[ `throw` ](../../language-reference/keywords/throw.md) Instrukcji **zgłasza** wyjątek. Wykonanie bieżącego zablokować kończy się, a także kontrolować przenosi do pierwszego dopasowania `catch` bloku znalezione w stosie wywołań. Następnie dodasz `catch` bloku w celu przetestowania tego kodu jest nieco później.

Konstruktor należy uzyskać jednej zmiany, tak, aby dodaje początkowej transakcji, a nie bezpośrednio aktualizowanie równowagi. Ponieważ wpisano już `MakeDeposit` metody wywoływania go z konstruktora. Zakończono konstruktora powinien wyglądać następująco:

[!code-csharp[Constructor](../../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType> jest właściwością, która zwraca bieżącą datę i godzinę. To przetestować, dodając kilka depozyty i wycofywania w swojej `Main` metody:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

Następnie przetestuj, przechwytującej warunki błędów by próbować utworzyć konto w serwisie ujemne saldo:

```csharp
// Test that the initial balances must be positive:
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

Możesz użyć [ `try` i `catch` instrukcji](../../language-reference/keywords/try-catch.md) zaznaczania bloku kodu, który może zgłaszać wyjątki i przechwytywać te błędy, których można oczekiwać. Można użyć tej samej techniki, aby przetestować kod, który zgłasza wyjątek salda ujemnego:

```csharp
// Test for a negative balance
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

Zapisywanie pliku i typu `dotnet run` do wypróbowania tej funkcji.

## <a name="challenge---log-all-transactions"></a>Rzuć wyzwanie — Rejestruj wszystkie transakcje

Aby zakończyć w tym samouczku, można napisać `GetAccountHistory` metodę umożliwiającą utworzenie `string` historii transakcji. Dodaj tę metodę w celu `BankAccount` typu:

[!code-csharp[History](../../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Ta metoda korzysta z <xref:System.Text.StringBuilder> klasy, aby sformatować ciąg, który zawiera jeden wiersz dla każdej transakcji. Ciąg formatowania kodu wcześniej w tych samouczkach przedstawiono. Jest jeden znak nowego `\t`. Który wstawia odpowiednią kartę, aby sformatować dane wyjściowe.

Dodaj następujący wiersz, aby przetestować go w **Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Typ `dotnet run` aby zobaczyć wyniki.

## <a name="next-steps"></a>Następne kroki

Jeśli użytkownik został zablokowany, widać źródła, w tym samouczku [w naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)

Gratulacje, zostały ukończone wszystkie nasze wprowadzenie do C# samouczków. Jeśli chcesz dowiedzieć się więcej, spróbuj jeden z naszych [samouczki](../index.md)
