---
title: Wprowadzenie do samouczka klasy - C# lokalnego poradniki Szybki Start
description: Utwórz pierwszy program C# i eksplorowanie obiektowej pojęcia
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: a951c84396e187b5ef1a832705b7722f818c990b
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457336"
---
# <a name="introduction-to-classes"></a><span data-ttu-id="7f7dd-103">Wprowadzenie do klas</span><span class="sxs-lookup"><span data-stu-id="7f7dd-103">Introduction to classes</span></span>

<span data-ttu-id="7f7dd-104">Ta opcja szybkiego startu oczekuje, że maszynie, która służy do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-104">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="7f7dd-105">Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="7f7dd-106">Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego poradniki Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-106">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="7f7dd-107">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7f7dd-107">Create your application</span></span>

<span data-ttu-id="7f7dd-108">Przy użyciu okno terminalu, Utwórz katalog o nazwie **klasy**.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-108">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="7f7dd-109">Aplikacja będzie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-109">You'll build your application there.</span></span> <span data-ttu-id="7f7dd-110">Przejdź do tego katalogu i wpisz `dotnet new console` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="7f7dd-111">To polecenie tworzy aplikację.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-111">This command creates your application.</span></span> <span data-ttu-id="7f7dd-112">Otwórz **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-112">Open **Program.cs**.</span></span> <span data-ttu-id="7f7dd-113">Go powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-113">It should look like this:</span></span>

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

<span data-ttu-id="7f7dd-114">W tym szybkiego startu możesz zacząć tworzyć nowe typy, które reprezentują konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-114">In this quickstart, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="7f7dd-115">Zwykle programiści określają każdej klasy w pliku tekstowym inny.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="7f7dd-116">Który ułatwia zarządzanie wraz z rozwojem programu rozmiar.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-116">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="7f7dd-117">Utwórz nowy plik o nazwie **BankAccount.cs** w **klasy** katalogu.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-117">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="7f7dd-118">Ten plik będzie zawierać definicję ***konta bankowego***.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="7f7dd-119">Obiekt programowania Oriented organizuje kodu przez tworzenie typów w formie ***klasy***.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="7f7dd-120">Tych klas zawiera kod, który reprezentuje określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="7f7dd-121">`BankAccount` Klasa reprezentuje konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="7f7dd-122">Kod implementuje określonych operacji za pomocą metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="7f7dd-123">Ta opcja szybkiego startu konta bankowego obsługuje tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-123">In this quickstart, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="7f7dd-124">Składa się z 10-cyfrowy numer, który unikatowo identyfikuje konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="7f7dd-125">Ma ona ciąg, który przechowuje nazwę lub nazwy właścicieli.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="7f7dd-126">Saldo może zostać pobrany.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="7f7dd-127">Akceptuje depozyty.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-127">It accepts deposits.</span></span>
1. <span data-ttu-id="7f7dd-128">Akceptuje wycofanie.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="7f7dd-129">Bilans początkowy musi być dodatnia.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="7f7dd-130">Wycofanie nie może być ujemna równowagi.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="7f7dd-131">Określ typ konta bankowego</span><span class="sxs-lookup"><span data-stu-id="7f7dd-131">Define the bank account type</span></span>

<span data-ttu-id="7f7dd-132">Można uruchomić tworzenia podstawy klasy definiującej tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="7f7dd-133">Go będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-133">It would look like this:</span></span>

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

<span data-ttu-id="7f7dd-134">Przed przejściem, Spójrzmy na został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="7f7dd-135">`namespace` Deklaracji umożliwia organizację kodu.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="7f7dd-136">Ta opcja szybkiego startu jest stosunkowo mały, więc będzie umieścić cały kod w jednym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-136">This quickstart is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="7f7dd-137">`public class BankAccount` definiuje klasę lub typ tworzony.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="7f7dd-138">Wszystkie elementy wewnątrz `{` i `}` następujący klasy deklaracji definiuje zachowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-138">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="7f7dd-139">Istnieje pięć ***członków*** z `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="7f7dd-140">Pierwsze trzy są ***właściwości***.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-140">The first three are ***properties***.</span></span> <span data-ttu-id="7f7dd-141">Właściwości elementów danych i może mieć kod, który wymusza sprawdzania poprawności lub inne zasady.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="7f7dd-142">Ostatnie dwa są ***metody***.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-142">The last two are ***methods***.</span></span> <span data-ttu-id="7f7dd-143">Bloki kodu, wykonujących jednej funkcji są metody.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="7f7dd-144">Odczytywanie nazwy wszystkich członków powinien podać informacji wystarczających lub innego projektanta zrozumieć, co oznacza klasy.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="7f7dd-145">Otwórz nowe konto</span><span class="sxs-lookup"><span data-stu-id="7f7dd-145">Open a new account</span></span>

<span data-ttu-id="7f7dd-146">Pierwszy funkcja do wykonania jest otworzyć konto.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="7f7dd-147">Gdy klient otworzy konto, musisz podać saldo początkowej oraz informacje o właściciela lub właścicieli tego konta.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="7f7dd-148">Tworzenie nowego obiektu `BankAccount` typu, oznacza to zdefiniowanie ***Konstruktor*** który przypisuje tych wartości.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="7f7dd-149">A ***konstruktora*** jest element członkowski, który ma taką samą nazwę jak klasa.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="7f7dd-150">Służy do zainicjowania obiekty tego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="7f7dd-151">Dodaj następujący Konstruktor do `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="7f7dd-152">Konstruktory są wywoływane podczas tworzenia obiektów przy użyciu [ `new` ](../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="7f7dd-152">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="7f7dd-153">Zastąp linię `Console.WriteLine("Hello World!");` w ***program.cs*** o następujący wiersz (Zastąp `<name>` nazwą):</span><span class="sxs-lookup"><span data-stu-id="7f7dd-153">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="7f7dd-154">Typ `dotnet run` aby zobaczyć, co się stanie.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="7f7dd-155">Zwróć uwagę, że numer konta jest puste?</span><span class="sxs-lookup"><span data-stu-id="7f7dd-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="7f7dd-156">Nadszedł czas, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-156">It's time to fix that.</span></span> <span data-ttu-id="7f7dd-157">Numer konta należy przydzielić podczas konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="7f7dd-158">Ale nie powinien być odpowiedzialność obiekt wywołujący, aby go utworzyć.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="7f7dd-159">`BankAccount` Kod klasy wiedzieć, jak można przypisać nowe numery kont.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="7f7dd-160">Prosty sposób, w tym celu ma rozpoczynać się od 10-cyfrowy numer.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="7f7dd-161">Zwiększenia po utworzeniu każdego nowego konta.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-161">Increment it when each new account is created.</span></span> <span data-ttu-id="7f7dd-162">Na koniec należy zapisać bieżący numer konta, gdy obiekt jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="7f7dd-163">Dodaj następujące deklaracji elementu członkowskiego do `BankAccount` klasy:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="7f7dd-164">Jest to element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-164">This is a data member.</span></span> <span data-ttu-id="7f7dd-165">Ma ona `private`, co oznacza, że można uzyskać tylko przez kod wewnątrz `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="7f7dd-166">Jest to sposób rozdzielenia obowiązków publicznej (np. o numer konta) z prywatna implementacja (jak numery kont są generowane.) Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="7f7dd-167">Typ `dotnet run` wyników.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-167">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="7f7dd-168">Utwórz wpłat i wycofania</span><span class="sxs-lookup"><span data-stu-id="7f7dd-168">Create deposits and withdrawals</span></span>

<span data-ttu-id="7f7dd-169">Klasa konta bankowego musi zaakceptować wpłat i wycofania działała prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-169">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="7f7dd-170">Umożliwia wdrożenie wpłat i wycofania przez utworzenie dziennika dla każdej transakcji dla konta.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-170">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="7f7dd-171">Który ma kilka zalet w porównaniu z po prostu aktualizowanie saldo każdą transakcję.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-171">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="7f7dd-172">Historia może służyć do inspekcji wszystkich transakcji i zarządzanie nimi salda dzienne.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-172">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="7f7dd-173">Przez obliczenie saldo z historii transakcji w razie potrzeby, wszelkie błędy w ramach jednej transakcji, które zostały usunięte zostaną poprawnie odzwierciedlone w Saldo na obliczenia dalej.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-173">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="7f7dd-174">Zacznijmy od utworzenia nowego typu do reprezentowania transakcji.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-174">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="7f7dd-175">To jest typem prostym, która nie ma żadnych obowiązki.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-175">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="7f7dd-176">Musi on kilka właściwości.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-176">It needs a few properties.</span></span> <span data-ttu-id="7f7dd-177">Utwórz nowy plik o nazwie ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-177">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="7f7dd-178">Dodaj do niej następujący kod:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-178">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="7f7dd-179">Teraz Dodajmy <xref:System.Collections.Generic.List%601> z `Transaction` obiekty do `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-179">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="7f7dd-180">Dodaj następujące oświadczenie:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-180">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="7f7dd-181"><xref:System.Collections.Generic.List%601> Klasy, musisz zaimportować inną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-181">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="7f7dd-182">Dodaj następujący kod na początku **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-182">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="7f7dd-183">Teraz Zmieńmy jak `Balance` został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-183">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="7f7dd-184">Można je znaleźć jako suma wartości wszystkich transakcji.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-184">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="7f7dd-185">Modyfikowanie deklaracja `Balance` w `BankAccount` klasy do następującego:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-185">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="7f7dd-186">W tym przykładzie pokazano ważnym aspektem ***właściwości***.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-186">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="7f7dd-187">Saldo jest teraz wykrywanie, gdy inny programisty poprosi o podanie wartości.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-187">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="7f7dd-188">Z obliczeń wylicza wszystkie transakcje i zapewnia Suma jako bieżące saldo.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-188">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="7f7dd-189">Następnie należy zaimplementować `MakeDeposit` i `MakeWithdrawal` metody.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-189">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="7f7dd-190">Tych metod będzie wymuszać końcowego dwie reguły: czy bilans początkowy musi być dodatnia i cofnięciu nie mogą tworzyć saldo ujemne.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-190">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="7f7dd-191">To pojęcia związane z ***wyjątki***.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-191">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="7f7dd-192">Standardowy sposób wskazujący, że metoda nie może pomyślnie wykonać pracę jest do zgłoszenia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-192">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="7f7dd-193">Typ wyjątku i komunikat skojarzony z nim opis błędu.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-193">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="7f7dd-194">W tym miejscu `MakeDeposit` metoda zgłasza wyjątek, jeśli ilość złożenia jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-194">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="7f7dd-195">`MakeWithdrawal` Metoda zgłasza wyjątek, jeśli kwota wycofania jest ujemny lub stosowania wycofanie powoduje saldo ujemne:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-195">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="7f7dd-196">[ `throw` ](../language-reference/keywords/throw.md) Instrukcji **zgłasza** Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-196">The [`throw`](../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="7f7dd-197">Kończy wykonywanie bieżącej metody i zostanie wznowiona, gdy odpowiadającego mu `catch` bloku został znaleziony.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-197">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="7f7dd-198">Należy dodać `catch` blok do przetestowania tego kodu nieco później.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-198">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="7f7dd-199">Konstruktora należy uzyskać jednej zmiany, dzięki czemu dodaje transakcję początkową, a nie bezpośrednio aktualizowanie saldo.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-199">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="7f7dd-200">Ponieważ już zapisano `MakeDeposit` metody wywołać ją z sieci konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-200">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="7f7dd-201">Zakończono Konstruktor powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-201">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="7f7dd-202"><xref:System.DateTime.Now?displayProperty=nameWithType> jest właściwością, która zwraca bieżącą datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-202"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="7f7dd-203">Testowania tej funkcji, dodając kilka wpłat i wycofywania w Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-203">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="7f7dd-204">Następnie testu, że są Przechwytywanie warunki błędów przez próby utworzenia konta z saldo ujemne:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-204">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="7f7dd-205">Możesz użyć [ `try` i `catch` instrukcje](../language-reference/keywords/try-catch.md) aby blok kodu, który może zgłaszać wyjątki i catch te błędy, które można spodziewać się.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-205">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="7f7dd-206">Tę samą metodę można użyć do testowania kodu, która zgłasza salda ujemnego:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-206">You can use the same technique to test the code that throws for a negative balance:</span></span>

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

<span data-ttu-id="7f7dd-207">Zapisz plik i typ `dotnet run` Wypróbuj ją.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-207">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="7f7dd-208">Test — zalogować wszystkich transakcji</span><span class="sxs-lookup"><span data-stu-id="7f7dd-208">Challenge - log all transactions</span></span>

<span data-ttu-id="7f7dd-209">Do zakończenia tego przewodnika Szybki Start, można napisać `GetAccountHistory` metodę, która tworzy `string` historii transakcji.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-209">To finish this quickstart, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="7f7dd-210">Dodaj tę metodę w celu `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-210">add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="7f7dd-211">Ta metoda korzysta <xref:System.Text.StringBuilder> klasy formatującej ciąg, który zawiera jeden wiersz dla każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-211">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="7f7dd-212">Przedstawiono ciągu formatowania kodu we wcześniejszej części te przewodniki Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-212">You've seen the string formatting code earlier in these quickstarts.</span></span> <span data-ttu-id="7f7dd-213">Jest jeden znak nowego `\t`.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-213">One new character is `\t`.</span></span> <span data-ttu-id="7f7dd-214">Która wstawia kartę, aby sformatować dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-214">That inserts a tab to format the output.</span></span>

<span data-ttu-id="7f7dd-215">Dodaj następujący wiersz do testowania w **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="7f7dd-215">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="7f7dd-216">Typ `dotnet run` wyników.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-216">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7f7dd-217">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7f7dd-217">Next Steps</span></span>

<span data-ttu-id="7f7dd-218">Jeśli użytkownik został zablokowany, można wyświetlić źródła dla tego przewodnika Szybki Start [w naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="7f7dd-218">If you got stuck, you can see the source for this quickstart [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="7f7dd-219">Gratulacje, po zakończeniu wszystkich naszych Przewodniki Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="7f7dd-219">Congratulations, you've finished all our Quickstarts.</span></span> <span data-ttu-id="7f7dd-220">Jeśli chcesz dowiedzieć się więcej, spróbuj naszych [samouczki](../tutorials/index.md)</span><span class="sxs-lookup"><span data-stu-id="7f7dd-220">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>
