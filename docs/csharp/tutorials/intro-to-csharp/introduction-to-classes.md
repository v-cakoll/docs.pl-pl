---
title: Klasy i obiekty — wprowadzenie do C# samouczka
description: Utwórz pierwszy C# program i Eksploruj koncepcje zorientowane obiektowo
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 06d1a30abc0d031badcba4ec60f7deb3c670a3ae
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634953"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="f0eee-103">Eksploruj programowanie zorientowane obiektowo przy użyciu klas i obiektów</span><span class="sxs-lookup"><span data-stu-id="f0eee-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="f0eee-104">Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="f0eee-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="f0eee-105">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="f0eee-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="f0eee-106">Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.</span><span class="sxs-lookup"><span data-stu-id="f0eee-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="f0eee-107">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="f0eee-107">Create your application</span></span>

<span data-ttu-id="f0eee-108">Za pomocą okna terminalu Utwórz katalog o nazwie *Classes*.</span><span class="sxs-lookup"><span data-stu-id="f0eee-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="f0eee-109">W tym miejscu utworzysz aplikację.</span><span class="sxs-lookup"><span data-stu-id="f0eee-109">You'll build your application there.</span></span> <span data-ttu-id="f0eee-110">Przejdź do tego katalogu i wpisz `dotnet new console` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="f0eee-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="f0eee-111">To polecenie tworzy aplikację.</span><span class="sxs-lookup"><span data-stu-id="f0eee-111">This command creates your application.</span></span> <span data-ttu-id="f0eee-112">Otwórz *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="f0eee-112">Open *Program.cs*.</span></span> <span data-ttu-id="f0eee-113">Jego powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f0eee-113">It should look like this:</span></span>

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

<span data-ttu-id="f0eee-114">W tym samouczku utworzysz nowe typy reprezentujące konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="f0eee-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="f0eee-115">Zazwyczaj deweloperzy definiują każdą klasę w innym pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="f0eee-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="f0eee-116">Ułatwia to zarządzanie w miarę zwiększania się rozmiaru programu.</span><span class="sxs-lookup"><span data-stu-id="f0eee-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="f0eee-117">Utwórz nowy plik o nazwie *BankAccount.cs* w katalogu *Classes* .</span><span class="sxs-lookup"><span data-stu-id="f0eee-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span> 

<span data-ttu-id="f0eee-118">Ten plik będzie zawierać definicję ***konta bankowego***.</span><span class="sxs-lookup"><span data-stu-id="f0eee-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="f0eee-119">Programowanie zorientowane obiektowo organizuje kod przez tworzenie typów w postaci ***klas***.</span><span class="sxs-lookup"><span data-stu-id="f0eee-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="f0eee-120">Klasy te zawierają kod, który reprezentuje konkretną jednostkę.</span><span class="sxs-lookup"><span data-stu-id="f0eee-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="f0eee-121">Klasa `BankAccount` reprezentuje konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="f0eee-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="f0eee-122">Kod implementuje określone operacje za pomocą metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0eee-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="f0eee-123">W tym samouczku konto bankowe obsługuje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="f0eee-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="f0eee-124">Ma 10-cyfrowy numer, który jednoznacznie identyfikuje konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="f0eee-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="f0eee-125">Zawiera on ciąg przechowujący nazwę lub nazwy właścicieli.</span><span class="sxs-lookup"><span data-stu-id="f0eee-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="f0eee-126">Można pobrać saldo.</span><span class="sxs-lookup"><span data-stu-id="f0eee-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="f0eee-127">Akceptuje ona depozyty.</span><span class="sxs-lookup"><span data-stu-id="f0eee-127">It accepts deposits.</span></span>
1. <span data-ttu-id="f0eee-128">Akceptuje on wycofania.</span><span class="sxs-lookup"><span data-stu-id="f0eee-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="f0eee-129">Saldo początkowe musi mieć wartość dodatnią.</span><span class="sxs-lookup"><span data-stu-id="f0eee-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="f0eee-130">Wycofanie nie może spowodować negatywnego salda.</span><span class="sxs-lookup"><span data-stu-id="f0eee-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="f0eee-131">Definiowanie typu konta bankowego</span><span class="sxs-lookup"><span data-stu-id="f0eee-131">Define the bank account type</span></span>

<span data-ttu-id="f0eee-132">Można rozpocząć od utworzenia podstawowych podstaw klasy, które definiują takie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f0eee-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="f0eee-133">Będzie to wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f0eee-133">It would look like this:</span></span>

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

<span data-ttu-id="f0eee-134">Przed rozpoczęciem przejdźmy do tego, co zostało skompilowane.</span><span class="sxs-lookup"><span data-stu-id="f0eee-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="f0eee-135">Deklaracja `namespace` zapewnia sposób logicznego organizowania kodu.</span><span class="sxs-lookup"><span data-stu-id="f0eee-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="f0eee-136">Ten samouczek jest stosunkowo mały, więc umieścisz cały kod w jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f0eee-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="f0eee-137">`public class BankAccount` definiuje klasę lub typ, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="f0eee-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="f0eee-138">Wszystko wewnątrz `{` i `}`, które następuje po deklaracji klasy, definiuje stan i zachowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="f0eee-138">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="f0eee-139">Istnieje pięć ***członków*** klasy `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="f0eee-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="f0eee-140">Pierwsze trzy są ***właściwościami***.</span><span class="sxs-lookup"><span data-stu-id="f0eee-140">The first three are ***properties***.</span></span> <span data-ttu-id="f0eee-141">Właściwości są elementami danych i mogą mieć kod, który wymusza walidację lub inne reguły.</span><span class="sxs-lookup"><span data-stu-id="f0eee-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="f0eee-142">Ostatnie dwa są ***metodami***.</span><span class="sxs-lookup"><span data-stu-id="f0eee-142">The last two are ***methods***.</span></span> <span data-ttu-id="f0eee-143">Metody to bloki kodu, które wykonują pojedynczą funkcję.</span><span class="sxs-lookup"><span data-stu-id="f0eee-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="f0eee-144">Odczytywanie nazw każdego z członków powinno zapewnić wystarczającą ilość informacji dla Ciebie lub innego dewelopera, aby zrozumieć, co robi Klasa.</span><span class="sxs-lookup"><span data-stu-id="f0eee-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="f0eee-145">Otwórz nowe konto</span><span class="sxs-lookup"><span data-stu-id="f0eee-145">Open a new account</span></span>

<span data-ttu-id="f0eee-146">Pierwsza funkcja do wdrożenia polega na otwarciu konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="f0eee-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="f0eee-147">Gdy klient otworzy konto, musi podać początkowe saldo i informacje o właścicielu lub właściciele tego konta.</span><span class="sxs-lookup"><span data-stu-id="f0eee-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="f0eee-148">Tworzenie nowego obiektu typu `BankAccount` oznacza zdefiniowanie ***konstruktora*** , który przypisuje te wartości.</span><span class="sxs-lookup"><span data-stu-id="f0eee-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="f0eee-149">***Konstruktor*** jest członkiem, który ma taką samą nazwę jak Klasa.</span><span class="sxs-lookup"><span data-stu-id="f0eee-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="f0eee-150">Służy do inicjowania obiektów tego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="f0eee-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="f0eee-151">Dodaj następujący Konstruktor do typu `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="f0eee-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="f0eee-152">Konstruktory są wywoływane podczas tworzenia obiektu przy użyciu [`new`](../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f0eee-152">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="f0eee-153">Zastąp wiersz `Console.WriteLine("Hello World!");` w *program.cs* następującym kodem (zastąp `<name>` nazwą):</span><span class="sxs-lookup"><span data-stu-id="f0eee-153">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="f0eee-154">Wpisz `dotnet run`, aby zobaczyć, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="f0eee-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="f0eee-155">Czy na pewno numer konta jest pusty?</span><span class="sxs-lookup"><span data-stu-id="f0eee-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="f0eee-156">Czas na rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="f0eee-156">It's time to fix that.</span></span> <span data-ttu-id="f0eee-157">Numer konta powinien być przypisany podczas konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0eee-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="f0eee-158">Ale nie powinien być odpowiedzialny za utworzenie go przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="f0eee-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="f0eee-159">Kod klasy `BankAccount` powinien wiedzieć, jak przypisać nowe numery kont.</span><span class="sxs-lookup"><span data-stu-id="f0eee-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="f0eee-160">Prostym sposobem, aby to zrobić, jest rozpoczęcie z 10-cyfrową liczbą.</span><span class="sxs-lookup"><span data-stu-id="f0eee-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="f0eee-161">Zwiększ ją po utworzeniu każdego nowego konta.</span><span class="sxs-lookup"><span data-stu-id="f0eee-161">Increment it when each new account is created.</span></span> <span data-ttu-id="f0eee-162">Na koniec Zapisz bieżący numer konta w przypadku konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0eee-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="f0eee-163">Dodaj następującą deklarację elementu członkowskiego do klasy `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="f0eee-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="f0eee-164">To jest element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="f0eee-164">This is a data member.</span></span> <span data-ttu-id="f0eee-165">Jest `private`, co oznacza, że dostęp do niego jest możliwy tylko przez kod wewnątrz klasy `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="f0eee-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="f0eee-166">Jest to sposób oddzielenia publicznych obowiązków (na przykład numeru konta) od implementacji prywatnej (jak są generowane numery kont).</span><span class="sxs-lookup"><span data-stu-id="f0eee-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="f0eee-167">Jest on również `static`, co oznacza, że jest współużytkowany przez wszystkie obiekty `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="f0eee-167">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="f0eee-168">Wartość zmiennej niestatycznej jest unikatowa dla każdego wystąpienia obiektu `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="f0eee-168">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="f0eee-169">Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:</span><span class="sxs-lookup"><span data-stu-id="f0eee-169">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="f0eee-170">Wpisz `dotnet run`, aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="f0eee-170">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="f0eee-171">Utwórz depozyty i Wycofaj</span><span class="sxs-lookup"><span data-stu-id="f0eee-171">Create deposits and withdrawals</span></span>

<span data-ttu-id="f0eee-172">Twoja Klasa konta bankowego musi akceptować depozyty i wycofywania, aby działały prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="f0eee-172">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="f0eee-173">Zaimplementujmy depozyty i wycofania, tworząc arkusz każdej transakcji dla konta.</span><span class="sxs-lookup"><span data-stu-id="f0eee-173">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="f0eee-174">Ma kilka korzyści w porównaniu do zwykłego aktualizowania salda każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="f0eee-174">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="f0eee-175">Historia może służyć do inspekcji wszystkich transakcji i zarządzania bilansami dziennymi.</span><span class="sxs-lookup"><span data-stu-id="f0eee-175">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="f0eee-176">Dzięki wykorzystaniu salda z historii wszystkich transakcji, gdy jest to potrzebne, wszelkie błędy w pojedynczej transakcji, które są stałe, zostaną prawidłowo odzwierciedlone w saldzie następnego obliczenia.</span><span class="sxs-lookup"><span data-stu-id="f0eee-176">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="f0eee-177">Zacznijmy od utworzenia nowego typu do reprezentowania transakcji.</span><span class="sxs-lookup"><span data-stu-id="f0eee-177">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="f0eee-178">Jest to prosty typ, który nie ma żadnych obowiązków.</span><span class="sxs-lookup"><span data-stu-id="f0eee-178">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="f0eee-179">Potrzebuje on kilku właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0eee-179">It needs a few properties.</span></span> <span data-ttu-id="f0eee-180">Utwórz nowy plik o nazwie *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="f0eee-180">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="f0eee-181">Dodaj do niej następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f0eee-181">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="f0eee-182">Teraz Dodajmy <xref:System.Collections.Generic.List%601> obiektów `Transaction` do klasy `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="f0eee-182">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="f0eee-183">Dodaj następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="f0eee-183">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](~/samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="f0eee-184">Klasa <xref:System.Collections.Generic.List%601> wymaga zaimportowania innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f0eee-184">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="f0eee-185">Dodaj następujące elementy na początku *BankAccount.cs*:</span><span class="sxs-lookup"><span data-stu-id="f0eee-185">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="f0eee-186">Teraz Zmieńmy sposób zgłaszania `Balance`.</span><span class="sxs-lookup"><span data-stu-id="f0eee-186">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="f0eee-187">Można go znaleźć, sumując wartości wszystkich transakcji.</span><span class="sxs-lookup"><span data-stu-id="f0eee-187">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="f0eee-188">Zmodyfikuj deklarację `Balance` w klasie `BankAccount` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f0eee-188">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="f0eee-189">Ten przykład pokazuje istotny aspekt ***Właściwości***.</span><span class="sxs-lookup"><span data-stu-id="f0eee-189">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="f0eee-190">Teraz trwa obliczanie salda, gdy inny programista pyta o wartość.</span><span class="sxs-lookup"><span data-stu-id="f0eee-190">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="f0eee-191">Wyliczenie wylicza wszystkie transakcje i zawiera sumę jako bieżące saldo.</span><span class="sxs-lookup"><span data-stu-id="f0eee-191">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="f0eee-192">Następnie Zaimplementuj metody `MakeDeposit` i `MakeWithdrawal`.</span><span class="sxs-lookup"><span data-stu-id="f0eee-192">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="f0eee-193">Te metody wymuszą dwie ostatnie reguły: początkowe saldo musi być dodatnie i że każde wycofanie nie może utworzyć salda ujemnego.</span><span class="sxs-lookup"><span data-stu-id="f0eee-193">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="f0eee-194">Wprowadza to koncepcję ***wyjątków***.</span><span class="sxs-lookup"><span data-stu-id="f0eee-194">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="f0eee-195">Standardowy sposób wskazujący, że metoda nie może zakończyć pracy, to zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f0eee-195">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="f0eee-196">Typ wyjątku i komunikat skojarzony z nim opisują błąd.</span><span class="sxs-lookup"><span data-stu-id="f0eee-196">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="f0eee-197">W tym miejscu Metoda `MakeDeposit` zgłasza wyjątek, jeśli kwota depozytu jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="f0eee-197">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="f0eee-198">Metoda `MakeWithdrawal` zgłasza wyjątek, jeśli kwota wycofania jest ujemna lub w przypadku zastosowania wycofania powoduje ujemne saldo:</span><span class="sxs-lookup"><span data-stu-id="f0eee-198">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="f0eee-199">Instrukcja [`throw`](../../language-reference/keywords/throw.md) **zgłasza** wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f0eee-199">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="f0eee-200">Wykonanie bieżącego bloku i sterowanie transferami do pierwszego pasującego bloku `catch` znalezionego w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="f0eee-200">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="f0eee-201">Dodasz blok `catch`, aby przetestować ten kod nieco później.</span><span class="sxs-lookup"><span data-stu-id="f0eee-201">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="f0eee-202">Konstruktor powinien otrzymać jedną zmianę, aby dodać początkową transakcję zamiast bezpośrednio aktualizować saldo.</span><span class="sxs-lookup"><span data-stu-id="f0eee-202">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="f0eee-203">Ponieważ zapisałeś już metodę `MakeDeposit`, wywołaj ją z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f0eee-203">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="f0eee-204">Gotowy Konstruktor powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f0eee-204">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="f0eee-205"><xref:System.DateTime.Now?displayProperty=nameWithType> to właściwość zwracająca bieżącą datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="f0eee-205"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="f0eee-206">Przetestuj to poprzez dodanie kilku depozytów i wycofaeń w metodzie `Main`:</span><span class="sxs-lookup"><span data-stu-id="f0eee-206">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="f0eee-207">Następnie należy sprawdzić, czy są przechwytywane warunki błędów, próbując utworzyć konto z ujemną wartością:</span><span class="sxs-lookup"><span data-stu-id="f0eee-207">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="f0eee-208">[Instrukcje`try` i `catch`](../../language-reference/keywords/try-catch.md) umożliwiają oznaczenie bloku kodu, który może generować wyjątki i przechwytywać te błędy, których oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="f0eee-208">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="f0eee-209">Możesz użyć tej samej techniki, aby przetestować kod, który zgłasza wyjątek dla nieujemnego salda:</span><span class="sxs-lookup"><span data-stu-id="f0eee-209">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

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

<span data-ttu-id="f0eee-210">Zapisz plik i wpisz `dotnet run`, aby go wypróbować.</span><span class="sxs-lookup"><span data-stu-id="f0eee-210">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="f0eee-211">Wyzwanie — Rejestruj wszystkie transakcje</span><span class="sxs-lookup"><span data-stu-id="f0eee-211">Challenge - log all transactions</span></span>

<span data-ttu-id="f0eee-212">Aby ukończyć ten samouczek, można napisać metodę `GetAccountHistory`, która tworzy `string` dla historii transakcji.</span><span class="sxs-lookup"><span data-stu-id="f0eee-212">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="f0eee-213">Dodaj tę metodę do typu `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="f0eee-213">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="f0eee-214">Używa klasy <xref:System.Text.StringBuilder> do formatowania ciągu, który zawiera jeden wiersz dla każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="f0eee-214">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="f0eee-215">W tych samouczkach pojawił się kod formatowania ciągu.</span><span class="sxs-lookup"><span data-stu-id="f0eee-215">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="f0eee-216">Jeden nowy znak jest `\t`.</span><span class="sxs-lookup"><span data-stu-id="f0eee-216">One new character is `\t`.</span></span> <span data-ttu-id="f0eee-217">Spowoduje to wstawienie karty w celu sformatowania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f0eee-217">That inserts a tab to format the output.</span></span>

<span data-ttu-id="f0eee-218">Dodaj ten wiersz, aby przetestować go w *program.cs*:</span><span class="sxs-lookup"><span data-stu-id="f0eee-218">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="f0eee-219">Wpisz `dotnet run`, aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="f0eee-219">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f0eee-220">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f0eee-220">Next steps</span></span>

<span data-ttu-id="f0eee-221">Jeśli zawiesz, że możesz zobaczyć źródło tego samouczka [w naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span><span class="sxs-lookup"><span data-stu-id="f0eee-221">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="f0eee-222">Gratulacje, udało Ci się ukończyć wszystkie nasze wprowadzenie C# do samouczków.</span><span class="sxs-lookup"><span data-stu-id="f0eee-222">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="f0eee-223">Jeśli eager chcesz dowiedzieć się więcej, wypróbuj więcej naszych [samouczków](../index.md).</span><span class="sxs-lookup"><span data-stu-id="f0eee-223">If you're eager to learn more, try more of our [tutorials](../index.md).</span></span>
