---
title: Wprowadzenie do klas — samouczek — C# lokalnego przewodników Szybki Start
description: Tworzenie pierwszego programu C# i Eksploruj pojęcia zorientowana obiektowo
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: c4eadfc431eb263777bf2b4543746f778dabb466
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347919"
---
# <a name="introduction-to-classes"></a><span data-ttu-id="da1a7-103">Wprowadzenie do klas</span><span class="sxs-lookup"><span data-stu-id="da1a7-103">Introduction to classes</span></span>

<span data-ttu-id="da1a7-104">Ten przewodnik Szybki Start oczekuje, że masz maszyny, których można użyć do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da1a7-104">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="da1a7-105">Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux.</span><span class="sxs-lookup"><span data-stu-id="da1a7-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="da1a7-106">Krótkie omówienie poleceń użyjesz znajduje się w [wprowadzenie do lokalnego przewodników Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="da1a7-106">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="da1a7-107">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="da1a7-107">Create your application</span></span>

<span data-ttu-id="da1a7-108">Za pomocą okna terminalu Utwórz katalog o nazwie **klasy**.</span><span class="sxs-lookup"><span data-stu-id="da1a7-108">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="da1a7-109">Skompiluj aplikację istnieje.</span><span class="sxs-lookup"><span data-stu-id="da1a7-109">You'll build your application there.</span></span> <span data-ttu-id="da1a7-110">Przejdź do tego katalogu i wpisz `dotnet new console` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="da1a7-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="da1a7-111">To polecenie umożliwia utworzenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da1a7-111">This command creates your application.</span></span> <span data-ttu-id="da1a7-112">Otwórz **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="da1a7-112">Open **Program.cs**.</span></span> <span data-ttu-id="da1a7-113">Jego powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="da1a7-113">It should look like this:</span></span>

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

<span data-ttu-id="da1a7-114">W tym przewodniku Szybki Start możesz zacząć tworzyć nowe typy, które reprezentują konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="da1a7-114">In this quickstart, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="da1a7-115">Zwykle deweloperzy określają każdej klasy w pliku tekstowym różne.</span><span class="sxs-lookup"><span data-stu-id="da1a7-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="da1a7-116">Ułatwia zarządzanie wzrostem program rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="da1a7-116">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="da1a7-117">Utwórz nowy plik o nazwie **BankAccount.cs** w **klasy** katalogu.</span><span class="sxs-lookup"><span data-stu-id="da1a7-117">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="da1a7-118">Ten plik będzie zawierać definicję ***konta bankowego***.</span><span class="sxs-lookup"><span data-stu-id="da1a7-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="da1a7-119">Obiekt programowania Oriented organizuje kodu, tworząc typów w formie ***klasy***.</span><span class="sxs-lookup"><span data-stu-id="da1a7-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="da1a7-120">Te klasy zawierają kod, który reprezentuje określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="da1a7-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="da1a7-121">`BankAccount` Klasa reprezentuje konto.</span><span class="sxs-lookup"><span data-stu-id="da1a7-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="da1a7-122">Kod implementuje określonych operacji w ramach metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="da1a7-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="da1a7-123">W tym przewodniku Szybki Start konta bankowego obsługuje to zachowanie:</span><span class="sxs-lookup"><span data-stu-id="da1a7-123">In this quickstart, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="da1a7-124">Posiada 10-cyfrowy numer, który unikatowo identyfikuje koncie bankowym.</span><span class="sxs-lookup"><span data-stu-id="da1a7-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="da1a7-125">Ciąg, który przechowuje nazwę lub nazwy właścicieli w nim.</span><span class="sxs-lookup"><span data-stu-id="da1a7-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="da1a7-126">Mogą być pobierane równowagi.</span><span class="sxs-lookup"><span data-stu-id="da1a7-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="da1a7-127">Akceptuje depozyty.</span><span class="sxs-lookup"><span data-stu-id="da1a7-127">It accepts deposits.</span></span>
1. <span data-ttu-id="da1a7-128">Akceptuje wycofywania.</span><span class="sxs-lookup"><span data-stu-id="da1a7-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="da1a7-129">Saldo początkowe musi być dodatnia.</span><span class="sxs-lookup"><span data-stu-id="da1a7-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="da1a7-130">Wycofanie nie może być ujemna równowagi.</span><span class="sxs-lookup"><span data-stu-id="da1a7-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="da1a7-131">Definiowanie typu konta bankowego</span><span class="sxs-lookup"><span data-stu-id="da1a7-131">Define the bank account type</span></span>

<span data-ttu-id="da1a7-132">Możesz rozpocząć od utworzenia podstawy klasy, która definiuje to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="da1a7-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="da1a7-133">Wyglądałby następująco:</span><span class="sxs-lookup"><span data-stu-id="da1a7-133">It would look like this:</span></span>

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

<span data-ttu-id="da1a7-134">Przed przejściem, Spójrzmy na wcześniej skompilowana.</span><span class="sxs-lookup"><span data-stu-id="da1a7-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="da1a7-135">`namespace` Deklaracja umożliwia organizację kodu.</span><span class="sxs-lookup"><span data-stu-id="da1a7-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="da1a7-136">Ten przewodnik Szybki Start jest stosunkowo mały, więc cały kod zostanie umieszczony w jednym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="da1a7-136">This quickstart is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="da1a7-137">`public class BankAccount` definiuje klasę lub typ tworzenia.</span><span class="sxs-lookup"><span data-stu-id="da1a7-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="da1a7-138">Wszystko wewnątrz `{` i `}` następujący klasy deklaracja określa zachowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="da1a7-138">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="da1a7-139">Istnieje pięć ***członków*** z `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="da1a7-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="da1a7-140">Pierwsze trzy są ***właściwości***.</span><span class="sxs-lookup"><span data-stu-id="da1a7-140">The first three are ***properties***.</span></span> <span data-ttu-id="da1a7-141">Właściwości elementów danych i może mieć kod, który wymusza sprawdzania poprawności lub inne zasady.</span><span class="sxs-lookup"><span data-stu-id="da1a7-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="da1a7-142">Ostatnie dwa są ***metody***.</span><span class="sxs-lookup"><span data-stu-id="da1a7-142">The last two are ***methods***.</span></span> <span data-ttu-id="da1a7-143">Metody to bloki kodu, które wykonują pojedynczą funkcję.</span><span class="sxs-lookup"><span data-stu-id="da1a7-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="da1a7-144">Odczytywanie nazwy każdego z członków powinien zapewnić odpowiednią ilość informacji w lub innemu deweloperowi, aby zrozumieć działanie klasy.</span><span class="sxs-lookup"><span data-stu-id="da1a7-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="da1a7-145">Otwórz nowe konto</span><span class="sxs-lookup"><span data-stu-id="da1a7-145">Open a new account</span></span>

<span data-ttu-id="da1a7-146">Pierwszą funkcją do zaimplementowania jest aby otworzyć konto.</span><span class="sxs-lookup"><span data-stu-id="da1a7-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="da1a7-147">Gdy klient otworzy konto, musisz podać początkowego salda i informacji o właściciela lub właścicieli tego konta.</span><span class="sxs-lookup"><span data-stu-id="da1a7-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="da1a7-148">Tworzenie nowego obiektu `BankAccount` typu polega na zdefiniowaniu ***Konstruktor*** , przypisuje tych wartości.</span><span class="sxs-lookup"><span data-stu-id="da1a7-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="da1a7-149">A ***Konstruktor*** jest elementem członkowskim, który ma taką samą nazwę jak klasa.</span><span class="sxs-lookup"><span data-stu-id="da1a7-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="da1a7-150">Służy do inicjowania obiektów tego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="da1a7-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="da1a7-151">Dodaj następującego konstruktora do `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="da1a7-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="da1a7-152">Konstruktory są wywoływane podczas tworzenia obiektu przy użyciu [ `new` ](../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="da1a7-152">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="da1a7-153">Zastąp wiersz `Console.WriteLine("Hello World!");` w ***program.cs*** o następujący wiersz (Zastąp `<name>` z Twoją nazwą):</span><span class="sxs-lookup"><span data-stu-id="da1a7-153">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="da1a7-154">Typ `dotnet run` aby zobaczyć, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="da1a7-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="da1a7-155">Zwróć uwagę, że numer konta jest puste?</span><span class="sxs-lookup"><span data-stu-id="da1a7-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="da1a7-156">Nadszedł czas, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="da1a7-156">It's time to fix that.</span></span> <span data-ttu-id="da1a7-157">Powinien zostać przypisany numer konta, gdy obiekt jest konstruowany.</span><span class="sxs-lookup"><span data-stu-id="da1a7-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="da1a7-158">Ale nie powinny być odpowiedzialność obiekt wywołujący, aby go utworzyć.</span><span class="sxs-lookup"><span data-stu-id="da1a7-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="da1a7-159">`BankAccount` Kod klasy wiedzieć, jak przypisać nowy numery kont.</span><span class="sxs-lookup"><span data-stu-id="da1a7-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="da1a7-160">Najprościej można to zrobić, jest zaczynać się cyfrą 10 cyfr.</span><span class="sxs-lookup"><span data-stu-id="da1a7-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="da1a7-161">Zwiększyć jej, po utworzeniu każdego nowego konta.</span><span class="sxs-lookup"><span data-stu-id="da1a7-161">Increment it when each new account is created.</span></span> <span data-ttu-id="da1a7-162">Na koniec należy zapisać numer bieżącego konta, gdy obiekt jest konstruowany.</span><span class="sxs-lookup"><span data-stu-id="da1a7-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="da1a7-163">Dodaj następującą deklarację elementu członkowskiego do `BankAccount` klasy:</span><span class="sxs-lookup"><span data-stu-id="da1a7-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="da1a7-164">Jest to element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="da1a7-164">This is a data member.</span></span> <span data-ttu-id="da1a7-165">Ma ona `private`, co oznacza, że może zostać oceniony jedynie przez kod wewnątrz `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="da1a7-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="da1a7-166">Jest to sposób rozdzielania obowiązków publiczny (takie jak obsługa numer konta) z prywatnej implementacji (jak numery kont są generowane.) Warto również `static`, co oznacza, że jest współużytkowana przez wszystkie ``BankAccount`` obiektów.</span><span class="sxs-lookup"><span data-stu-id="da1a7-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) It is also `static`, which means it is shared by all of the ``BankAccount`` objects.</span></span> <span data-ttu-id="da1a7-167">Wartość zmiennej niestatycznych jest unikatowy dla każdego wystąpienia ``BankAccount`` obiektu.</span><span class="sxs-lookup"><span data-stu-id="da1a7-167">The value of a non-static variable is unique to each instance of the ``BankAccount`` object.</span></span> <span data-ttu-id="da1a7-168">Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:</span><span class="sxs-lookup"><span data-stu-id="da1a7-168">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="da1a7-169">Typ `dotnet run` aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="da1a7-169">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="da1a7-170">Utwórz wpłat i wycofanie</span><span class="sxs-lookup"><span data-stu-id="da1a7-170">Create deposits and withdrawals</span></span>

<span data-ttu-id="da1a7-171">Klasa konta bankowego musi zaakceptować wpłat i wycofania do prawidłowego działania.</span><span class="sxs-lookup"><span data-stu-id="da1a7-171">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="da1a7-172">Umożliwia Implementowanie wpłat i wycofanie, tworząc dziennik każdej transakcji dla konta.</span><span class="sxs-lookup"><span data-stu-id="da1a7-172">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="da1a7-173">Który ma kilka zalet w stosunku do zaktualizowania saldu każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="da1a7-173">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="da1a7-174">Można historię inspekcji wszystkich transakcji i zarządzanie nimi salda dzienne.</span><span class="sxs-lookup"><span data-stu-id="da1a7-174">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="da1a7-175">Za obliczenia równowagi z historii wszystkich transakcji, gdy potrzebne, wszelkie błędy w ramach jednej transakcji, które zostały usunięte zostaną prawidłowo odzwierciedlone w równowagi na następny obliczeń.</span><span class="sxs-lookup"><span data-stu-id="da1a7-175">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="da1a7-176">Zacznijmy od utworzenia nowego typu do reprezentowania transakcji.</span><span class="sxs-lookup"><span data-stu-id="da1a7-176">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="da1a7-177">Jest to prosty typ, który nie ma żadnych obowiązki.</span><span class="sxs-lookup"><span data-stu-id="da1a7-177">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="da1a7-178">Musi ona kilka właściwości.</span><span class="sxs-lookup"><span data-stu-id="da1a7-178">It needs a few properties.</span></span> <span data-ttu-id="da1a7-179">Utwórz nowy plik o nazwie ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="da1a7-179">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="da1a7-180">Dodaj następujący kod do niego:</span><span class="sxs-lookup"><span data-stu-id="da1a7-180">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="da1a7-181">Teraz Dodajmy <xref:System.Collections.Generic.List%601> z `Transaction` obiekty do `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="da1a7-181">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="da1a7-182">Dodaj następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="da1a7-182">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="da1a7-183"><xref:System.Collections.Generic.List%601> Klasy, musisz zaimportować innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="da1a7-183">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="da1a7-184">Dodaj następujący kod na początku **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="da1a7-184">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="da1a7-185">Teraz zmienimy sposób, w jaki `Balance` są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="da1a7-185">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="da1a7-186">Można je znaleźć przez zsumowanie wartości wszystkich transakcji.</span><span class="sxs-lookup"><span data-stu-id="da1a7-186">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="da1a7-187">Zmodyfikuj deklarację zmiennej `Balance` w `BankAccount` klasy do następującego:</span><span class="sxs-lookup"><span data-stu-id="da1a7-187">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="da1a7-188">W tym przykładzie przedstawiono istotnym elementem ***właściwości***.</span><span class="sxs-lookup"><span data-stu-id="da1a7-188">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="da1a7-189">Saldo jest teraz obliczeń, gdy programista innego poprosi o podanie wartości.</span><span class="sxs-lookup"><span data-stu-id="da1a7-189">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="da1a7-190">Twoje obliczeń wylicza wszystkie transakcje oraz zapewnia Suma jako bieżące saldo.</span><span class="sxs-lookup"><span data-stu-id="da1a7-190">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="da1a7-191">Następnie należy zaimplementować `MakeDeposit` i `MakeWithdrawal` metody.</span><span class="sxs-lookup"><span data-stu-id="da1a7-191">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="da1a7-192">Tych metod będzie wymuszać końcowego dwie reguły: czy saldo początkowe musi być liczbą dodatnią, a każde wystąpienie nie mogą tworzyć saldo ujemne.</span><span class="sxs-lookup"><span data-stu-id="da1a7-192">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="da1a7-193">Wprowadza pojęcia ***wyjątki***.</span><span class="sxs-lookup"><span data-stu-id="da1a7-193">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="da1a7-194">Standardowy sposób wskazujący, że metody nie może ukończyć swojej pracy pomyślnie jest zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="da1a7-194">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="da1a7-195">Typ wyjątku i komunikat skojarzony z nim opisuje błąd.</span><span class="sxs-lookup"><span data-stu-id="da1a7-195">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="da1a7-196">W tym miejscu `MakeDeposit` metoda zgłasza wyjątek, jeśli ilość złożenia jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="da1a7-196">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="da1a7-197">`MakeWithdrawal` Metoda zgłasza wyjątek, jeśli kwota wycofania jest ujemna, czy stosowanie wycofanie skutkuje ujemne saldo:</span><span class="sxs-lookup"><span data-stu-id="da1a7-197">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="da1a7-198">[ `throw` ](../language-reference/keywords/throw.md) Instrukcji **zgłasza** wyjątek.</span><span class="sxs-lookup"><span data-stu-id="da1a7-198">The [`throw`](../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="da1a7-199">Kończy wykonywanie bieżącej metody i zostanie wznowiona po pasujący obiekt typu `catch` blok zostanie znaleziony.</span><span class="sxs-lookup"><span data-stu-id="da1a7-199">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="da1a7-200">Następnie dodasz `catch` bloku w celu przetestowania tego kodu jest nieco później.</span><span class="sxs-lookup"><span data-stu-id="da1a7-200">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="da1a7-201">Konstruktor należy uzyskać jednej zmiany, tak, aby dodaje początkowej transakcji, a nie bezpośrednio aktualizowanie równowagi.</span><span class="sxs-lookup"><span data-stu-id="da1a7-201">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="da1a7-202">Ponieważ wpisano już `MakeDeposit` metody wywoływania go z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="da1a7-202">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="da1a7-203">Zakończono konstruktora powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="da1a7-203">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="da1a7-204"><xref:System.DateTime.Now?displayProperty=nameWithType> jest właściwością, która zwraca bieżącą datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="da1a7-204"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="da1a7-205">To przetestować, dodając kilka depozyty i wycofywania w swojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="da1a7-205">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="da1a7-206">Następnie przetestuj, przechwytującej warunki błędów by próbować utworzyć konto w serwisie ujemne saldo:</span><span class="sxs-lookup"><span data-stu-id="da1a7-206">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="da1a7-207">Możesz użyć [ `try` i `catch` instrukcji](../language-reference/keywords/try-catch.md) zaznaczania bloku kodu, który może zgłaszać wyjątki i przechwytywać te błędy, których można oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="da1a7-207">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="da1a7-208">Można użyć tej samej techniki, aby przetestować kod, który zgłasza salda ujemnego:</span><span class="sxs-lookup"><span data-stu-id="da1a7-208">You can use the same technique to test the code that throws for a negative balance:</span></span>

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

<span data-ttu-id="da1a7-209">Zapisywanie pliku i typu `dotnet run` do wypróbowania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="da1a7-209">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="da1a7-210">Rzuć wyzwanie — Rejestruj wszystkie transakcje</span><span class="sxs-lookup"><span data-stu-id="da1a7-210">Challenge - log all transactions</span></span>

<span data-ttu-id="da1a7-211">Aby ukończyć ten przewodnik Szybki Start, możesz napisać `GetAccountHistory` metodę umożliwiającą utworzenie `string` historii transakcji.</span><span class="sxs-lookup"><span data-stu-id="da1a7-211">To finish this quickstart, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="da1a7-212">Dodaj tę metodę w celu `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="da1a7-212">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="da1a7-213">Ta metoda korzysta z <xref:System.Text.StringBuilder> klasy, aby sformatować ciąg, który zawiera jeden wiersz dla każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="da1a7-213">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="da1a7-214">Ciąg formatowania kodu wcześniej w tych przewodników Szybki Start przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="da1a7-214">You've seen the string formatting code earlier in these quickstarts.</span></span> <span data-ttu-id="da1a7-215">Jest jeden znak nowego `\t`.</span><span class="sxs-lookup"><span data-stu-id="da1a7-215">One new character is `\t`.</span></span> <span data-ttu-id="da1a7-216">Który wstawia odpowiednią kartę, aby sformatować dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="da1a7-216">That inserts a tab to format the output.</span></span>

<span data-ttu-id="da1a7-217">Dodaj następujący wiersz, aby przetestować go w **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="da1a7-217">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="da1a7-218">Typ `dotnet run` aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="da1a7-218">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="da1a7-219">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="da1a7-219">Next Steps</span></span>

<span data-ttu-id="da1a7-220">Jeśli użytkownik został zablokowany, możesz zobaczyć źródła dla tego przewodnika Szybki Start [w naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="da1a7-220">If you got stuck, you can see the source for this quickstart [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="da1a7-221">Gratulacje, zostały ukończone wszystkie naszymi przewodnikami szybkiego startu.</span><span class="sxs-lookup"><span data-stu-id="da1a7-221">Congratulations, you've finished all our Quickstarts.</span></span> <span data-ttu-id="da1a7-222">Jeśli chcesz dowiedzieć się więcej, spróbuj naszych [samouczki](../tutorials/index.md)</span><span class="sxs-lookup"><span data-stu-id="da1a7-222">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>
