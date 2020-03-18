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
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="c20d3-103">Eksplorowanie programowania obiektowego za pomocą klas i obiektów</span><span class="sxs-lookup"><span data-stu-id="c20d3-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="c20d3-104">Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia.</span><span class="sxs-lookup"><span data-stu-id="c20d3-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="c20d3-105">Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="c20d3-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="c20d3-106">Szybki przegląd poleceń, których będziesz używać, znajduje się w [obszarze Zaznajomij się z narzędziami programistycznymi](local-environment.md) z łączami do szczegółowych informacji.</span><span class="sxs-lookup"><span data-stu-id="c20d3-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="c20d3-107">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c20d3-107">Create your application</span></span>

<span data-ttu-id="c20d3-108">Korzystając z okna terminala, utwórz katalog o nazwie *klasy*.</span><span class="sxs-lookup"><span data-stu-id="c20d3-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="c20d3-109">Stworzysz tam aplikację.</span><span class="sxs-lookup"><span data-stu-id="c20d3-109">You'll build your application there.</span></span> <span data-ttu-id="c20d3-110">Zmień ten katalog `dotnet new console` i wpisz w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c20d3-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="c20d3-111">To polecenie tworzy aplikację.</span><span class="sxs-lookup"><span data-stu-id="c20d3-111">This command creates your application.</span></span> <span data-ttu-id="c20d3-112">Otwórz *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="c20d3-112">Open *Program.cs*.</span></span> <span data-ttu-id="c20d3-113">Powinny wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c20d3-113">It should look like this:</span></span>

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

<span data-ttu-id="c20d3-114">W tym samouczku masz zamiar utworzyć nowe typy, które reprezentują konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="c20d3-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="c20d3-115">Zazwyczaj deweloperzy definiują każdą klasę w innym pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="c20d3-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="c20d3-116">To sprawia, że łatwiej zarządzać w miarę wzrostu rozmiaru programu.</span><span class="sxs-lookup"><span data-stu-id="c20d3-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="c20d3-117">Utwórz nowy plik o nazwie *BankAccount.cs* w katalogu *klas.*</span><span class="sxs-lookup"><span data-stu-id="c20d3-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="c20d3-118">Ten plik będzie zawierał definicję ***konta bankowego***.</span><span class="sxs-lookup"><span data-stu-id="c20d3-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="c20d3-119">Programowanie obiektowe organizuje kod, tworząc typy w postaci ***klas***.</span><span class="sxs-lookup"><span data-stu-id="c20d3-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="c20d3-120">Klasy te zawierają kod, który reprezentuje określoną jednostkę.</span><span class="sxs-lookup"><span data-stu-id="c20d3-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="c20d3-121">Klasa `BankAccount` reprezentuje konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="c20d3-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="c20d3-122">Kod implementuje określone operacje za pomocą metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="c20d3-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="c20d3-123">W tym samouczku konto bankowe obsługuje to zachowanie:</span><span class="sxs-lookup"><span data-stu-id="c20d3-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="c20d3-124">Posiada 10-cyfrowy numer, który jednoznacznie identyfikuje konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="c20d3-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="c20d3-125">Ma ciąg, który przechowuje nazwę lub nazwy właścicieli.</span><span class="sxs-lookup"><span data-stu-id="c20d3-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="c20d3-126">Saldo można pobrać.</span><span class="sxs-lookup"><span data-stu-id="c20d3-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="c20d3-127">Przyjmuje depozyty.</span><span class="sxs-lookup"><span data-stu-id="c20d3-127">It accepts deposits.</span></span>
1. <span data-ttu-id="c20d3-128">Akceptuje wypłaty.</span><span class="sxs-lookup"><span data-stu-id="c20d3-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="c20d3-129">Saldo początkowe musi być dodatnie.</span><span class="sxs-lookup"><span data-stu-id="c20d3-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="c20d3-130">Wypłaty nie mogą skutkować ujemnym saldem.</span><span class="sxs-lookup"><span data-stu-id="c20d3-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="c20d3-131">Definiowanie typu konta bankowego</span><span class="sxs-lookup"><span data-stu-id="c20d3-131">Define the bank account type</span></span>

<span data-ttu-id="c20d3-132">Można rozpocząć od utworzenia podstaw klasy, która definiuje to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="c20d3-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="c20d3-133">Wyglądałoby to tak:</span><span class="sxs-lookup"><span data-stu-id="c20d3-133">It would look like this:</span></span>

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

<span data-ttu-id="c20d3-134">Zanim przejdziesz dalej, przyjrzyjmy się temu, co zbudowałeś.</span><span class="sxs-lookup"><span data-stu-id="c20d3-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="c20d3-135">Deklaracja `namespace` zapewnia sposób logicznie zorganizować kod.</span><span class="sxs-lookup"><span data-stu-id="c20d3-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="c20d3-136">Ten samouczek jest stosunkowo mały, więc umieścisz cały kod w jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c20d3-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="c20d3-137">`public class BankAccount`definiuje klasę lub typ, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="c20d3-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="c20d3-138">Wszystko wewnątrz `{` `}` i że następuje deklaracja klasy definiuje stan i zachowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="c20d3-138">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="c20d3-139">Istnieje pięciu ***członków*** `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="c20d3-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="c20d3-140">Pierwsze trzy to ***właściwości***.</span><span class="sxs-lookup"><span data-stu-id="c20d3-140">The first three are ***properties***.</span></span> <span data-ttu-id="c20d3-141">Właściwości są elementami danych i może mieć kod, który wymusza sprawdzanie poprawności lub inne reguły.</span><span class="sxs-lookup"><span data-stu-id="c20d3-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="c20d3-142">Ostatnie dwie to ***metody***.</span><span class="sxs-lookup"><span data-stu-id="c20d3-142">The last two are ***methods***.</span></span> <span data-ttu-id="c20d3-143">Metody są bloki kodu, które wykonują jedną funkcję.</span><span class="sxs-lookup"><span data-stu-id="c20d3-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="c20d3-144">Czytanie nazw każdego z członków należy podać wystarczającą ilość informacji dla Ciebie lub innego dewelopera, aby zrozumieć, co robi klasa.</span><span class="sxs-lookup"><span data-stu-id="c20d3-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="c20d3-145">Otwieranie nowego konta</span><span class="sxs-lookup"><span data-stu-id="c20d3-145">Open a new account</span></span>

<span data-ttu-id="c20d3-146">Pierwszą funkcją do wdrożenia jest otwarcie konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="c20d3-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="c20d3-147">Gdy klient otwiera konto, musi podać początkowe saldo i informacje o właścicielu lub właścicielach tego konta.</span><span class="sxs-lookup"><span data-stu-id="c20d3-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="c20d3-148">Tworzenie nowego obiektu `BankAccount` typu oznacza definiowanie ***konstruktora,*** który przypisuje te wartości.</span><span class="sxs-lookup"><span data-stu-id="c20d3-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="c20d3-149">***Konstruktor*** jest elementem członkowskim, który ma taką samą nazwę jak klasa.</span><span class="sxs-lookup"><span data-stu-id="c20d3-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="c20d3-150">Służy do inicjowania obiektów tego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="c20d3-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="c20d3-151">Dodaj następujący konstruktor do `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="c20d3-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="c20d3-152">Konstruktory są wywoływane podczas [`new`](../../language-reference/operators/new-operator.md)tworzenia obiektu przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="c20d3-152">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="c20d3-153">Zastąp wiersz `Console.WriteLine("Hello World!");` w *Program.cs* `<name>` na następujący kod (zamień na swoje imię i nazwisko):</span><span class="sxs-lookup"><span data-stu-id="c20d3-153">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="c20d3-154">Wpisz, `dotnet run` aby zobaczyć, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="c20d3-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="c20d3-155">Czy zauważyłeś, że numer konta jest pusty?</span><span class="sxs-lookup"><span data-stu-id="c20d3-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="c20d3-156">Nadszedł czas, aby to naprawić.</span><span class="sxs-lookup"><span data-stu-id="c20d3-156">It's time to fix that.</span></span> <span data-ttu-id="c20d3-157">Numer konta powinien być przypisany, gdy obiekt jest skonstruowany.</span><span class="sxs-lookup"><span data-stu-id="c20d3-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="c20d3-158">Ale nie powinno być obowiązkiem dzwoniącego, aby go utworzyć.</span><span class="sxs-lookup"><span data-stu-id="c20d3-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="c20d3-159">Kod `BankAccount` klasy powinien wiedzieć, jak przypisać nowe numery kont.</span><span class="sxs-lookup"><span data-stu-id="c20d3-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="c20d3-160">Prostym sposobem na to jest zacząć od numeru 10-cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="c20d3-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="c20d3-161">Zwiększaj go podczas tworzenia każdego nowego konta.</span><span class="sxs-lookup"><span data-stu-id="c20d3-161">Increment it when each new account is created.</span></span> <span data-ttu-id="c20d3-162">Na koniec przechowuj numer bieżącego konta, gdy obiekt jest konstruowany.</span><span class="sxs-lookup"><span data-stu-id="c20d3-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="c20d3-163">Dodaj następującą deklarację `BankAccount` elementu członkowskiego do klasy:</span><span class="sxs-lookup"><span data-stu-id="c20d3-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="c20d3-164">Jest to element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="c20d3-164">This is a data member.</span></span> <span data-ttu-id="c20d3-165">Jest `private`, co oznacza, że jest dostępny tylko `BankAccount` przez kod wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="c20d3-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="c20d3-166">Jest to sposób oddzielenia obowiązków publicznych (np. posiadania numeru konta) od implementacji prywatnej (sposób generowania numerów kont).</span><span class="sxs-lookup"><span data-stu-id="c20d3-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="c20d3-167">Jest to `static`również , co oznacza, `BankAccount` że jest współużytkowany przez wszystkie obiekty.</span><span class="sxs-lookup"><span data-stu-id="c20d3-167">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="c20d3-168">Wartość zmiennej niestatycznej jest unikatowa `BankAccount` dla każdego wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="c20d3-168">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="c20d3-169">Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:</span><span class="sxs-lookup"><span data-stu-id="c20d3-169">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="c20d3-170">Wpisz, `dotnet run` aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="c20d3-170">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="c20d3-171">Tworzenie wpłat i wypłat</span><span class="sxs-lookup"><span data-stu-id="c20d3-171">Create deposits and withdrawals</span></span>

<span data-ttu-id="c20d3-172">Twoja klasa konta bankowego musi akceptować wpłaty i wypłaty, aby działały poprawnie.</span><span class="sxs-lookup"><span data-stu-id="c20d3-172">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="c20d3-173">Zaimplementujmy wpłaty i wypłaty, tworząc arkusz każdej transakcji dla konta.</span><span class="sxs-lookup"><span data-stu-id="c20d3-173">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="c20d3-174">To ma kilka zalet w porównaniu z po prostu aktualizacją salda każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="c20d3-174">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="c20d3-175">Historia może służyć do inspekcji wszystkich transakcji i zarządzania dziennymi saldami.</span><span class="sxs-lookup"><span data-stu-id="c20d3-175">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="c20d3-176">Obliczając saldo z historii wszystkich transakcji w razie potrzeby, wszelkie błędy w pojedynczej transakcji, które są stałe zostaną poprawnie odzwierciedlone w saldzie przy następnym obliczeniu.</span><span class="sxs-lookup"><span data-stu-id="c20d3-176">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="c20d3-177">Zacznijmy od utworzenia nowego typu do reprezentowania transakcji.</span><span class="sxs-lookup"><span data-stu-id="c20d3-177">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="c20d3-178">Jest to prosty typ, który nie ma żadnych obowiązków.</span><span class="sxs-lookup"><span data-stu-id="c20d3-178">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="c20d3-179">Potrzebuje kilku właściwości.</span><span class="sxs-lookup"><span data-stu-id="c20d3-179">It needs a few properties.</span></span> <span data-ttu-id="c20d3-180">Utwórz nowy plik o nazwie *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="c20d3-180">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="c20d3-181">Dodaj do niej następujący kod:</span><span class="sxs-lookup"><span data-stu-id="c20d3-181">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="c20d3-182">Teraz dodajmy <xref:System.Collections.Generic.List%601> obiekty `Transaction` do `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="c20d3-182">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="c20d3-183">Dodaj następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="c20d3-183">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="c20d3-184">Klasa <xref:System.Collections.Generic.List%601> wymaga zaimportowania innego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="c20d3-184">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="c20d3-185">Na początku *BankAccount.cs*dodaj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="c20d3-185">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="c20d3-186">Teraz zmieńmy sposób zgłaszania. `Balance`</span><span class="sxs-lookup"><span data-stu-id="c20d3-186">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="c20d3-187">Można go znaleźć, sumując wartości wszystkich transakcji.</span><span class="sxs-lookup"><span data-stu-id="c20d3-187">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="c20d3-188">Zmodyfikuj `Balance` `BankAccount` deklarację w klasie na:</span><span class="sxs-lookup"><span data-stu-id="c20d3-188">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="c20d3-189">W tym przykładzie przedstawiono ważny aspekt ***właściwości***.</span><span class="sxs-lookup"><span data-stu-id="c20d3-189">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="c20d3-190">Teraz obliczasz równowagę, gdy inny programista prosi o wartość.</span><span class="sxs-lookup"><span data-stu-id="c20d3-190">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="c20d3-191">Obliczenia wyliczają wszystkie transakcje i zawiera sumę jako bieżące saldo.</span><span class="sxs-lookup"><span data-stu-id="c20d3-191">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="c20d3-192">Następnie zaimplementuj `MakeDeposit` i `MakeWithdrawal` metody.</span><span class="sxs-lookup"><span data-stu-id="c20d3-192">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="c20d3-193">Metody te będą wymuszać dwie ostatnie zasady: że początkowe saldo musi być dodatnie i że każde wycofanie nie może stworzyć ujemnego salda.</span><span class="sxs-lookup"><span data-stu-id="c20d3-193">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="c20d3-194">Wprowadza to pojęcie ***wyjątków***.</span><span class="sxs-lookup"><span data-stu-id="c20d3-194">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="c20d3-195">Standardowy sposób wskazujący, że metoda nie może ukończyć pomyślnie swojej pracy jest zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c20d3-195">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="c20d3-196">Typ wyjątku i skojarzony z nim komunikat opisują błąd.</span><span class="sxs-lookup"><span data-stu-id="c20d3-196">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="c20d3-197">W tym `MakeDeposit` miejscu metoda zgłasza wyjątek, jeśli kwota depozytu jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="c20d3-197">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="c20d3-198">Metoda `MakeWithdrawal` zgłasza wyjątek, jeśli kwota wypłaty jest ujemna lub jeśli zastosowanie wypłaty powoduje ujemne saldo:</span><span class="sxs-lookup"><span data-stu-id="c20d3-198">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="c20d3-199">Instrukcja [`throw`](../../language-reference/keywords/throw.md) **zgłasza** wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c20d3-199">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="c20d3-200">Wykonywanie bieżącego bloku kończy się i kontroli `catch` transferów do pierwszego pasującego bloku znaleźć w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="c20d3-200">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="c20d3-201">Dodasz blok, `catch` aby przetestować ten kod nieco później.</span><span class="sxs-lookup"><span data-stu-id="c20d3-201">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="c20d3-202">Konstruktor powinien uzyskać jedną zmianę, tak aby dodaje transakcję początkową, a nie bezpośrednio aktualizować saldo.</span><span class="sxs-lookup"><span data-stu-id="c20d3-202">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="c20d3-203">Ponieważ metoda została `MakeDeposit` już zapisano, wywołaj ją z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c20d3-203">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="c20d3-204">Gotowy konstruktor powinien wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="c20d3-204">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="c20d3-205"><xref:System.DateTime.Now?displayProperty=nameWithType>jest właściwością, która zwraca bieżącą datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="c20d3-205"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="c20d3-206">Przetestuj to, dodając kilka wpłat i wypłat w swojej `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="c20d3-206">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="c20d3-207">Następnie sprawdź, czy są przechwytywanie warunków błędu, próbując utworzyć konto z ujemnym saldem:</span><span class="sxs-lookup"><span data-stu-id="c20d3-207">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="c20d3-208">Użyj [ `try` `catch` i instrukcje,](../../language-reference/keywords/try-catch.md) aby oznaczyć blok kodu, który może zgłaszać wyjątki i przechwycić te błędy, które można oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="c20d3-208">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="c20d3-209">Tej samej techniki można użyć do testowania kodu, który zgłasza wyjątek dla ujemnego salda:</span><span class="sxs-lookup"><span data-stu-id="c20d3-209">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

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

<span data-ttu-id="c20d3-210">Zapisz plik i `dotnet run` wpisz, aby go wypróbować.</span><span class="sxs-lookup"><span data-stu-id="c20d3-210">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="c20d3-211">Wyzwanie - rejestruj wszystkie transakcje</span><span class="sxs-lookup"><span data-stu-id="c20d3-211">Challenge - log all transactions</span></span>

<span data-ttu-id="c20d3-212">Aby zakończyć ten samouczek, można napisać `GetAccountHistory` metodę, która tworzy `string` dla historii transakcji.</span><span class="sxs-lookup"><span data-stu-id="c20d3-212">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="c20d3-213">Dodaj tę metodę `BankAccount` do typu:</span><span class="sxs-lookup"><span data-stu-id="c20d3-213">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="c20d3-214">Używa <xref:System.Text.StringBuilder> klasy do formatowania ciągu, który zawiera jeden wiersz dla każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="c20d3-214">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="c20d3-215">Widzieliście kod formatowania ciągu wcześniej w tych samouczkach.</span><span class="sxs-lookup"><span data-stu-id="c20d3-215">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="c20d3-216">Jedną z `\t`nowych postaci jest .</span><span class="sxs-lookup"><span data-stu-id="c20d3-216">One new character is `\t`.</span></span> <span data-ttu-id="c20d3-217">Wstawia kartę, aby sformatować dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c20d3-217">That inserts a tab to format the output.</span></span>

<span data-ttu-id="c20d3-218">Dodaj ten wiersz, aby przetestować go w *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="c20d3-218">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="c20d3-219">Wpisz, `dotnet run` aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="c20d3-219">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c20d3-220">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c20d3-220">Next steps</span></span>

<span data-ttu-id="c20d3-221">Jeśli utknąłeś, możesz zobaczyć źródło tego samouczka [w naszym reppo GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span><span class="sxs-lookup"><span data-stu-id="c20d3-221">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="c20d3-222">Gratulacje, zakończyłeś wszystkie nasze wprowadzenie do samouczków języka C#.</span><span class="sxs-lookup"><span data-stu-id="c20d3-222">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="c20d3-223">Jeśli chcesz dowiedzieć się więcej, spróbuj więcej naszych [tutoriali](../index.md).</span><span class="sxs-lookup"><span data-stu-id="c20d3-223">If you're eager to learn more, try more of our [tutorials](../index.md).</span></span>
