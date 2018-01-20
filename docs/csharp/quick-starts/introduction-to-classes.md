---
title: "Przewodnik Szybki Start — wprowadzenie do klasy - C#"
description: "Utwórz pierwszy program C# i eksplorowanie obiektowej pojęcia"
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4e15b1b12b9420ca1781eca3f2578fa24c9ec82a
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="introduction-to-classes"></a>Wprowadzenie do klas

To szybki start oczekuje, że masz maszynie, która służy do tworzenia aplikacji. Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux. Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.

## <a name="create-your-application"></a>Tworzenie aplikacji

Przy użyciu okno terminalu, Utwórz katalog o nazwie **klasy**. Aplikacja będzie kompilacji. Przejdź do tego katalogu i wpisz `dotnet new console` w oknie konsoli. To polecenie tworzy aplikację. Otwórz **Program.cs**. Go powinien wyglądać następująco:

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

W tym szybki start możesz zacząć tworzyć nowe typy, które reprezentują konta bankowego. Zwykle programiści określają każdej klasy w pliku tekstowym inny. Który ułatwia zarządzanie wraz z rozwojem programu rozmiar.  Utwórz nowy plik o nazwie **BankAccount.cs** w **klasy** katalogu. 

Ten plik będzie zawierać definicję ***konta bankowego***. Obiekt programowania Oriented organizuje kodu przez tworzenie typów w formie ***klasy***. Tych klas zawiera kod, który reprezentuje określonej jednostki. `BankAccount` Klasa reprezentuje konta bankowego. Kod implementuje określonych operacji za pomocą metody i właściwości. W tym szybki start konta bankowego obsługuje tego zachowania:

1. Składa się z 10-cyfrowy numer, który unikatowo identyfikuje konta bankowego.
1. Ma ona ciąg, który przechowuje nazwę lub nazwy właścicieli.
1. Saldo może zostać pobrany.
1. Akceptuje depozyty.
1. Akceptuje wycofanie.
1. Bilans początkowy musi być dodatnia.
1. Wycofanie nie może być ujemna równowagi.

## <a name="define-the-bank-account-type"></a>Określ typ konta bankowego

Można uruchomić tworzenia podstawy klasy definiującej tego zachowania. Go będzie wyglądać następująco:

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

Przed przejściem, Spójrzmy na został skompilowany.  `namespace` Deklaracji umożliwia organizację kodu. To szybki start jest stosunkowo mały, więc będzie umieścić cały kod w jednym obszarze nazw. 

`public class BankAccount`definiuje klasę lub typ tworzony. Wszystkie elementy wewnątrz `{` i `}` następujący klasy deklaracji definiuje zachowanie klasy. Istnieje pięć ***członków*** z `BankAccount` klasy. Pierwsze trzy są ***właściwości***. Właściwości elementów danych i może mieć kod, który wymusza sprawdzania poprawności lub inne zasady. Ostatnie dwa są ***metody***. Metody są bloki kodu tego administracją jednej funkcji. Odczytywanie nazwy wszystkich członków powinien podać informacji wystarczających lub innego projektanta zrozumieć, co oznacza klasy.

## <a name="open-a-new-account"></a>Otwórz nowe konto

Pierwszy funkcja do wykonania jest otworzyć konto. Gdy klient otworzy konto, musisz podać saldo początkowej oraz informacje o właściciela lub właścicieli tego konta. 

Tworzenie nowego obiektu `BankAccount` typu, oznacza to zdefiniowanie ***Konstruktor*** który przypisuje tych wartości. A ***konstruktora*** jest element członkowski, który ma taką samą nazwę jak klasa. Służy do zainicjowania obiekty tego typu klasy. Dodaj następujący Konstruktor do `BankAccount` typu:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory są wywoływane podczas tworzenia obiektów przy użyciu [ `new` ](../language-reference/keywords/new.md). Zastąp linię `Console.WriteLine("Hello World!");` w ***program.cs*** o następujący wiersz (Zastąp `<name>` nazwą):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Typ `dotnet run` aby zobaczyć, co się stanie.  

Zwróć uwagę, że numer konta jest puste? Nadszedł czas, aby rozwiązać ten problem. Numer konta należy przydzielić podczas konstruowania obiektu. Ale nie powinien być odpowiedzialność obiekt wywołujący, aby go utworzyć. `BankAccount` Kod klasy wiedzieć, jak można przypisać nowe numery kont.  Prosty sposób, w tym celu ma rozpoczynać się od 10-cyfrowy numer. Zwiększenia po utworzeniu każdego nowego konta. Na koniec należy zapisać bieżący numer konta, gdy obiekt jest tworzony.

Dodaj następujące deklaracji elementu członkowskiego do `BankAccount` klasy:

```csharp
private static int accountNumberSeed = 1234567890;
```

Jest to element członkowski danych. Ma ona `private`, co oznacza, że można uzyskać tylko przez kod wewnątrz `BankAccount` klasy. Jest to sposób rozdzielenia obowiązków publicznej (np. o numer konta) z prywatna implementacja (jak numery kont są generowane.) Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Typ `dotnet run` wyników.

## <a name="create-deposits-and-withdrawals"></a>Utwórz wpłat i wycofania

Klasa konta bankowego musi zaakceptować wpłat i wycofania działała prawidłowo. Umożliwia wdrożenie wpłat i wycofania przez utworzenie dziennika dla każdej transakcji dla konta. Który ma kilka zalet w porównaniu z po prostu aktualizowanie saldo każdą transakcję. Historia może służyć do inspekcji wszystkich transakcji i zarządzanie nimi salda dzienne. Przez obliczenie saldo z historii transakcji w razie potrzeby, wszelkie błędy w ramach jednej transakcji, które zostały usunięte zostaną poprawnie odzwierciedlone w Saldo na obliczenia dalej.

Zacznijmy od utworzenia nowego typu do reprezentowania transakcji. To jest typem prostym, która nie ma żadnych obowiązki. Musi on kilka właściwości. Utwórz nowy plik o nazwie ***Transaction.cs***. Dodaj do niej następujący kod:

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Teraz Dodajmy <xref:System.Collections.Generic.List%601> z `Transaction` obiekty do `BankAccount` klasy. Dodaj następujące oświadczenie:

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601> Klasy, musisz zaimportować inną przestrzeń nazw. Dodaj następujący kod na początku **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

Teraz Zmieńmy jak `Balance` został zgłoszony.  Można je znaleźć jako suma wartości wszystkich transakcji. Modyfikowanie deklaracja `Balance` w `BankAccount` klasy do następującego:

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

W tym przykładzie pokazano ważnym aspektem ***właściwości***. Saldo jest teraz wykrywanie, gdy inny programisty poprosi o podanie wartości. Z obliczeń wylicza wszystkie transakcje i zapewnia Suma jako bieżące saldo.

Następnie należy zaimplementować `MakeDeposit` i `MakeWithdrawal` metody. Tych metod będzie wymuszać końcowego dwie reguły: czy bilans początkowy musi być dodatnia i cofnięciu nie mogą tworzyć saldo ujemne. 

To pojęcia związane z ***wyjątki***. Standardowy sposób wskazujący, że metoda nie może pomyślnie wykonać pracę jest do zgłoszenia wyjątku. Typ wyjątku i komunikat skojarzony z nim opis błędu. W tym miejscu `MakeDeposit` metoda zgłasza wyjątek, jeśli ilość złożenia jest ujemna. `MakeWithdrawal` Metoda zgłasza wyjątek, jeśli kwota wycofania jest ujemny lub stosowania wycofanie powoduje saldo ujemne:

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

[ `throw` ](../language-reference/keywords/throw.md) Instrukcji **zgłasza** Wystąpił wyjątek. Kończy wykonywanie bieżącej metody i zostanie wznowiona, gdy odpowiadającego mu `catch` bloku został znaleziony. Należy dodać `catch` blok do przetestowania tego kodu nieco później.

Konstruktora należy uzyskać jednej zmiany, dzięki czemu dodaje transakcję początkową, a nie bezpośrednio aktualizowanie saldo. Ponieważ już zapisano `MakeDeposit` metody wywołać ją z sieci konstruktora. Zakończono Konstruktor powinien wyglądać następująco:

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType>jest właściwością, która zwraca bieżącą datę i godzinę. Testowania tej funkcji, dodając kilka wpłat i wycofywania w Twojej `Main` metody:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

Następnie testu, że są Przechwytywanie warunki błędów przez próby utworzenia konta z saldo ujemne:

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

Możesz użyć [ `try` i `catch` instrukcje](../language-reference/keywords/try-catch.md) aby blok kodu, który może zgłaszać wyjątki i catch te błędy, które można spodziewać się. Tę samą metodę można użyć do testowania kodu, która zgłasza salda ujemnego:

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

Zapisz plik i typ `dotnet run` Wypróbuj ją.

## <a name="challenge---log-all-transactions"></a>Test — zalogować wszystkich transakcji

Aby zakończyć to szybki start, można napisać `GetAccountHistory` metodę, która tworzy `string` historii transakcji. Dodaj tę metodę w celu `BankAccount` typu:

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Ta metoda korzysta <xref:System.Text.StringBuilder> klasy formatującej ciąg, który zawiera jeden wiersz dla każdej transakcji. Przedstawiono ciągu formatowania kodu we wcześniejszej części tych Szybki Start. Jest jeden znak nowego `\t`. Która wstawia kartę, aby sformatować dane wyjściowe.

Dodaj następujący wiersz do testowania w **Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Typ `dotnet run` wyników.

## <a name="next-steps"></a>Następne kroki

Jeśli użytkownik został zablokowany, można wyświetlić źródła dla tego szybki start [w naszym repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)

Gratulacje, po zakończeniu wszystkich naszych Szybki Start. Jeśli chcesz dowiedzieć się więcej, spróbuj naszych [samouczki](../tutorials/index.md)
