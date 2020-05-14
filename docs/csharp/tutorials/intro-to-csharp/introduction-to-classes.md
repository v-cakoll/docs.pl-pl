---
title: Klasy i obiekty — wprowadzenie do samouczka języka C#
description: Utwórz pierwszy program w języku C# i Eksploruj koncepcje zorientowane obiektowo
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 5edb2d7b11caace2d794b7958dfeb75ef502ee2b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396867"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="d9049-103">Eksploruj programowanie zorientowane obiektowo przy użyciu klas i obiektów</span><span class="sxs-lookup"><span data-stu-id="d9049-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="d9049-104">Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="d9049-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="d9049-105">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="d9049-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="d9049-106">Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.</span><span class="sxs-lookup"><span data-stu-id="d9049-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="d9049-107">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d9049-107">Create your application</span></span>

<span data-ttu-id="d9049-108">Za pomocą okna terminalu Utwórz katalog o nazwie *Classes*.</span><span class="sxs-lookup"><span data-stu-id="d9049-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="d9049-109">W tym miejscu utworzysz aplikację.</span><span class="sxs-lookup"><span data-stu-id="d9049-109">You'll build your application there.</span></span> <span data-ttu-id="d9049-110">Przejdź do tego katalogu i wpisz `dotnet new console` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="d9049-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="d9049-111">To polecenie tworzy aplikację.</span><span class="sxs-lookup"><span data-stu-id="d9049-111">This command creates your application.</span></span> <span data-ttu-id="d9049-112">Otwórz *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="d9049-112">Open *Program.cs*.</span></span> <span data-ttu-id="d9049-113">Powinny wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d9049-113">It should look like this:</span></span>

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

<span data-ttu-id="d9049-114">W tym samouczku utworzysz nowe typy reprezentujące konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="d9049-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="d9049-115">Zazwyczaj deweloperzy definiują każdą klasę w innym pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="d9049-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="d9049-116">Ułatwia to zarządzanie w miarę zwiększania się rozmiaru programu.</span><span class="sxs-lookup"><span data-stu-id="d9049-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="d9049-117">Utwórz nowy plik o nazwie *BankAccount.cs* w katalogu *Classes* .</span><span class="sxs-lookup"><span data-stu-id="d9049-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="d9049-118">Ten plik będzie zawierać definicję ***konta bankowego***.</span><span class="sxs-lookup"><span data-stu-id="d9049-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="d9049-119">Programowanie zorientowane obiektowo organizuje kod przez tworzenie typów w postaci ***klas***.</span><span class="sxs-lookup"><span data-stu-id="d9049-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="d9049-120">Klasy te zawierają kod, który reprezentuje konkretną jednostkę.</span><span class="sxs-lookup"><span data-stu-id="d9049-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="d9049-121">`BankAccount`Klasa reprezentuje konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="d9049-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="d9049-122">Kod implementuje określone operacje za pomocą metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9049-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="d9049-123">W tym samouczku konto bankowe obsługuje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="d9049-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="d9049-124">Ma 10-cyfrowy numer, który jednoznacznie identyfikuje konto bankowe.</span><span class="sxs-lookup"><span data-stu-id="d9049-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="d9049-125">Zawiera on ciąg przechowujący nazwę lub nazwy właścicieli.</span><span class="sxs-lookup"><span data-stu-id="d9049-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="d9049-126">Można pobrać saldo.</span><span class="sxs-lookup"><span data-stu-id="d9049-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="d9049-127">Akceptuje ona depozyty.</span><span class="sxs-lookup"><span data-stu-id="d9049-127">It accepts deposits.</span></span>
1. <span data-ttu-id="d9049-128">Akceptuje on wycofania.</span><span class="sxs-lookup"><span data-stu-id="d9049-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="d9049-129">Saldo początkowe musi mieć wartość dodatnią.</span><span class="sxs-lookup"><span data-stu-id="d9049-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="d9049-130">Wycofanie nie może spowodować negatywnego salda.</span><span class="sxs-lookup"><span data-stu-id="d9049-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="d9049-131">Definiowanie typu konta bankowego</span><span class="sxs-lookup"><span data-stu-id="d9049-131">Define the bank account type</span></span>

<span data-ttu-id="d9049-132">Można rozpocząć od utworzenia podstawowych podstaw klasy, które definiują takie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="d9049-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="d9049-133">Utwórz nowy plik przy użyciu polecenia **File: New** .</span><span class="sxs-lookup"><span data-stu-id="d9049-133">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="d9049-134">Nadaj mu nazwę *BankAccount.cs*.</span><span class="sxs-lookup"><span data-stu-id="d9049-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="d9049-135">Dodaj następujący kod do pliku *BankAccount.cs* :</span><span class="sxs-lookup"><span data-stu-id="d9049-135">Add the following code to your *BankAccount.cs* file:</span></span>

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

<span data-ttu-id="d9049-136">Przed rozpoczęciem przejdźmy do tego, co zostało skompilowane.</span><span class="sxs-lookup"><span data-stu-id="d9049-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="d9049-137">`namespace`Deklaracja umożliwia logicznie organizowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="d9049-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="d9049-138">Ten samouczek jest stosunkowo mały, więc umieścisz cały kod w jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d9049-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="d9049-139">`public class BankAccount`definiuje klasę lub typ, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="d9049-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="d9049-140">Wszystko wewnątrz `{` i `}` , które następuje po deklaracji klasy, definiuje stan i zachowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="d9049-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="d9049-141">Istnieje pięć ***członków*** `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="d9049-141">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="d9049-142">Pierwsze trzy są ***właściwościami***.</span><span class="sxs-lookup"><span data-stu-id="d9049-142">The first three are ***properties***.</span></span> <span data-ttu-id="d9049-143">Właściwości są elementami danych i mogą mieć kod, który wymusza walidację lub inne reguły.</span><span class="sxs-lookup"><span data-stu-id="d9049-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="d9049-144">Ostatnie dwa są ***metodami***.</span><span class="sxs-lookup"><span data-stu-id="d9049-144">The last two are ***methods***.</span></span> <span data-ttu-id="d9049-145">Metody to bloki kodu, które wykonują pojedynczą funkcję.</span><span class="sxs-lookup"><span data-stu-id="d9049-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="d9049-146">Odczytywanie nazw każdego z członków powinno zapewnić wystarczającą ilość informacji dla Ciebie lub innego dewelopera, aby zrozumieć, co robi Klasa.</span><span class="sxs-lookup"><span data-stu-id="d9049-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="d9049-147">Otwórz nowe konto</span><span class="sxs-lookup"><span data-stu-id="d9049-147">Open a new account</span></span>

<span data-ttu-id="d9049-148">Pierwsza funkcja do wdrożenia polega na otwarciu konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="d9049-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="d9049-149">Gdy klient otworzy konto, musi podać początkowe saldo i informacje o właścicielu lub właściciele tego konta.</span><span class="sxs-lookup"><span data-stu-id="d9049-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="d9049-150">Tworzenie nowego obiektu `BankAccount` typu oznacza zdefiniowanie ***konstruktora*** , który przypisuje te wartości.</span><span class="sxs-lookup"><span data-stu-id="d9049-150">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="d9049-151">***Konstruktor*** jest członkiem, który ma taką samą nazwę jak Klasa.</span><span class="sxs-lookup"><span data-stu-id="d9049-151">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="d9049-152">Służy do inicjowania obiektów tego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="d9049-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="d9049-153">Dodaj do typu następujący Konstruktor `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="d9049-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="d9049-154">Umieść poniższy kod powyżej deklaracji `MakeDeposit` :</span><span class="sxs-lookup"><span data-stu-id="d9049-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="d9049-155">Konstruktory są wywoływane podczas tworzenia obiektu za pomocą [`new`](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="d9049-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="d9049-156">Zastąp wiersz `Console.WriteLine("Hello World!");` w *program.cs* następującym kodem (Zastąp `<name>` nazwą):</span><span class="sxs-lookup"><span data-stu-id="d9049-156">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="d9049-157">Uruchommy te, które zostały już skompilowane.</span><span class="sxs-lookup"><span data-stu-id="d9049-157">Let's run what you've built so far.</span></span> <span data-ttu-id="d9049-158">Jeśli używasz programu Visual Studio, wybierz pozycję **Uruchom bez debugowania** z menu **Uruchom** .</span><span class="sxs-lookup"><span data-stu-id="d9049-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="d9049-159">Jeśli używasz wiersza polecenia, wpisz `dotnet run` w katalogu, w którym został utworzony projekt.</span><span class="sxs-lookup"><span data-stu-id="d9049-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="d9049-160">Czy na pewno numer konta jest pusty?</span><span class="sxs-lookup"><span data-stu-id="d9049-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="d9049-161">Czas na rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="d9049-161">It's time to fix that.</span></span> <span data-ttu-id="d9049-162">Numer konta powinien być przypisany podczas konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9049-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="d9049-163">Ale nie powinien być odpowiedzialny za utworzenie go przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="d9049-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="d9049-164">`BankAccount`Kod klasy powinien wiedzieć, jak przypisać nowe numery kont.</span><span class="sxs-lookup"><span data-stu-id="d9049-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="d9049-165">Prostym sposobem, aby to zrobić, jest rozpoczęcie z 10-cyfrową liczbą.</span><span class="sxs-lookup"><span data-stu-id="d9049-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="d9049-166">Zwiększ ją po utworzeniu każdego nowego konta.</span><span class="sxs-lookup"><span data-stu-id="d9049-166">Increment it when each new account is created.</span></span> <span data-ttu-id="d9049-167">Na koniec Zapisz bieżący numer konta w przypadku konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9049-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="d9049-168">Dodaj deklarację elementu członkowskiego do `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="d9049-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="d9049-169">Umieść następujący wiersz kodu po nawiasie otwierającym `{` na początku `BankAccount` klasy:</span><span class="sxs-lookup"><span data-stu-id="d9049-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="d9049-170">To jest element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="d9049-170">This is a data member.</span></span> <span data-ttu-id="d9049-171">Oznacza to `private` , że można uzyskać do niego dostęp tylko przez kod wewnątrz `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="d9049-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="d9049-172">Jest to sposób oddzielenia publicznych obowiązków (na przykład numeru konta) od implementacji prywatnej (jak są generowane numery kont).</span><span class="sxs-lookup"><span data-stu-id="d9049-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="d9049-173">Jest to również `static` , co oznacza, że jest ono współużytkowane przez wszystkie `BankAccount` obiekty.</span><span class="sxs-lookup"><span data-stu-id="d9049-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="d9049-174">Wartość zmiennej niestatycznej jest unikatowa dla każdego wystąpienia `BankAccount` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9049-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="d9049-175">Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta.</span><span class="sxs-lookup"><span data-stu-id="d9049-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="d9049-176">Umieść je po wierszu, który brzmi `this.Balance = initialBalance` :</span><span class="sxs-lookup"><span data-stu-id="d9049-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="d9049-177">Wpisz `dotnet run` , aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="d9049-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="d9049-178">Utwórz depozyty i Wycofaj</span><span class="sxs-lookup"><span data-stu-id="d9049-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="d9049-179">Twoja Klasa konta bankowego musi akceptować depozyty i wycofywania, aby działały prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="d9049-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="d9049-180">Zaimplementujmy depozyty i wycofania, tworząc arkusz każdej transakcji dla konta.</span><span class="sxs-lookup"><span data-stu-id="d9049-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="d9049-181">Ma kilka korzyści w porównaniu do zwykłego aktualizowania salda każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="d9049-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="d9049-182">Historia może służyć do inspekcji wszystkich transakcji i zarządzania bilansami dziennymi.</span><span class="sxs-lookup"><span data-stu-id="d9049-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="d9049-183">Dzięki wykorzystaniu salda z historii wszystkich transakcji, gdy jest to potrzebne, wszelkie błędy w pojedynczej transakcji, które są stałe, zostaną prawidłowo odzwierciedlone w saldzie następnego obliczenia.</span><span class="sxs-lookup"><span data-stu-id="d9049-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="d9049-184">Zacznijmy od utworzenia nowego typu do reprezentowania transakcji.</span><span class="sxs-lookup"><span data-stu-id="d9049-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="d9049-185">Jest to prosty typ, który nie ma żadnych obowiązków.</span><span class="sxs-lookup"><span data-stu-id="d9049-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="d9049-186">Potrzebuje on kilku właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9049-186">It needs a few properties.</span></span> <span data-ttu-id="d9049-187">Utwórz nowy plik o nazwie *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="d9049-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="d9049-188">Dodaj do niej następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d9049-188">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="d9049-189">Teraz Dodajmy <xref:System.Collections.Generic.List%601> `Transaction` obiekty do `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="d9049-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="d9049-190">Dodaj następującą deklarację po konstruktorze w pliku *BankAccount.cs* :</span><span class="sxs-lookup"><span data-stu-id="d9049-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="d9049-191"><xref:System.Collections.Generic.List%601>Klasa wymaga zaimportowania innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d9049-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="d9049-192">Dodaj następujące elementy na początku *BankAccount.cs*:</span><span class="sxs-lookup"><span data-stu-id="d9049-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="d9049-193">Teraz Zmieńmy sposób `Balance` zgłaszania raportu.</span><span class="sxs-lookup"><span data-stu-id="d9049-193">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="d9049-194">Można go znaleźć, sumując wartości wszystkich transakcji.</span><span class="sxs-lookup"><span data-stu-id="d9049-194">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="d9049-195">Zmodyfikuj deklarację `Balance` `BankAccount` klasy w klasie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d9049-195">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="d9049-196">Ten przykład pokazuje istotny aspekt ***Właściwości***.</span><span class="sxs-lookup"><span data-stu-id="d9049-196">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="d9049-197">Teraz trwa obliczanie salda, gdy inny programista pyta o wartość.</span><span class="sxs-lookup"><span data-stu-id="d9049-197">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="d9049-198">Wyliczenie wylicza wszystkie transakcje i zawiera sumę jako bieżące saldo.</span><span class="sxs-lookup"><span data-stu-id="d9049-198">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="d9049-199">Następnie Zaimplementuj `MakeDeposit` metody i `MakeWithdrawal` .</span><span class="sxs-lookup"><span data-stu-id="d9049-199">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="d9049-200">Te metody wymuszą dwie ostatnie reguły: początkowe saldo musi być dodatnie i że każde wycofanie nie może utworzyć salda ujemnego.</span><span class="sxs-lookup"><span data-stu-id="d9049-200">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="d9049-201">Wprowadza to koncepcję ***wyjątków***.</span><span class="sxs-lookup"><span data-stu-id="d9049-201">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="d9049-202">Standardowy sposób wskazujący, że metoda nie może zakończyć pracy, to zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d9049-202">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="d9049-203">Typ wyjątku i komunikat skojarzony z nim opisują błąd.</span><span class="sxs-lookup"><span data-stu-id="d9049-203">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="d9049-204">W tym miejscu `MakeDeposit` Metoda zgłasza wyjątek, jeśli kwota depozytu jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="d9049-204">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="d9049-205">`MakeWithdrawal`Metoda zgłasza wyjątek, jeśli kwota wycofania jest ujemna lub jeśli zastosowanie wycofania powoduje ujemne saldo.</span><span class="sxs-lookup"><span data-stu-id="d9049-205">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="d9049-206">Dodaj następujący kod po deklaracji `allTransactions` listy:</span><span class="sxs-lookup"><span data-stu-id="d9049-206">Add the following code after the declaration of the `allTransactions` list:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="d9049-207">[`throw`](../../language-reference/keywords/throw.md)Instrukcja **zgłasza** wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d9049-207">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="d9049-208">Wykonanie bieżącego bloku i sterowanie transferami do pierwszego zgodnego `catch` bloku znalezionego w stosie wywołań.</span><span class="sxs-lookup"><span data-stu-id="d9049-208">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="d9049-209">Dodasz blok, `catch` Aby przetestować ten kod nieco później.</span><span class="sxs-lookup"><span data-stu-id="d9049-209">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="d9049-210">Konstruktor powinien otrzymać jedną zmianę, aby dodać początkową transakcję zamiast bezpośrednio aktualizować saldo.</span><span class="sxs-lookup"><span data-stu-id="d9049-210">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="d9049-211">Ponieważ już zapisano `MakeDeposit` metodę, wywołaj ją z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d9049-211">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="d9049-212">Gotowy Konstruktor powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d9049-212">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="d9049-213"><xref:System.DateTime.Now?displayProperty=nameWithType>jest właściwością zwracającą bieżącą datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="d9049-213"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="d9049-214">Przetestuj to poprzez dodanie kilku depozytów i wycofań w `Main` metodzie, po kodzie, który tworzy nowy `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="d9049-214">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="d9049-215">Następnie należy sprawdzić, czy są przechwytywane warunki błędów, próbując utworzyć konto z równoważeniem minus.</span><span class="sxs-lookup"><span data-stu-id="d9049-215">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="d9049-216">Dodaj następujący kod po właśnie powyższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="d9049-216">Add the following code after the preceding code you just added:</span></span>

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

<span data-ttu-id="d9049-217">Za pomocą [ `try` `catch` instrukcji i](../../language-reference/keywords/try-catch.md) można oznaczyć blok kodu, który może generować wyjątki i przechwytywać te błędy, których oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="d9049-217">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="d9049-218">Możesz użyć tej samej techniki, aby przetestować kod, który zgłasza wyjątek dla salda ujemnego.</span><span class="sxs-lookup"><span data-stu-id="d9049-218">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="d9049-219">Dodaj następujący kod na końcu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d9049-219">Add the following code at the end of your `Main` method:</span></span>

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

<span data-ttu-id="d9049-220">Zapisz plik i wpisz, `dotnet run` Aby go wypróbować.</span><span class="sxs-lookup"><span data-stu-id="d9049-220">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="d9049-221">Wyzwanie — Rejestruj wszystkie transakcje</span><span class="sxs-lookup"><span data-stu-id="d9049-221">Challenge - log all transactions</span></span>

<span data-ttu-id="d9049-222">Aby ukończyć ten samouczek, można napisać `GetAccountHistory` metodę, która tworzy `string` dla historii transakcji.</span><span class="sxs-lookup"><span data-stu-id="d9049-222">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="d9049-223">Dodaj tę metodę do `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="d9049-223">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="d9049-224">Używa <xref:System.Text.StringBuilder> klasy do formatowania ciągu, który zawiera jeden wiersz dla każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="d9049-224">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="d9049-225">W tych samouczkach pojawił się kod formatowania ciągu.</span><span class="sxs-lookup"><span data-stu-id="d9049-225">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="d9049-226">Jeden nowy znak to `\t` .</span><span class="sxs-lookup"><span data-stu-id="d9049-226">One new character is `\t`.</span></span> <span data-ttu-id="d9049-227">Spowoduje to wstawienie karty w celu sformatowania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d9049-227">That inserts a tab to format the output.</span></span>

<span data-ttu-id="d9049-228">Dodaj ten wiersz, aby przetestować go w *program.cs*:</span><span class="sxs-lookup"><span data-stu-id="d9049-228">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="d9049-229">Uruchom program, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="d9049-229">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d9049-230">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d9049-230">Next steps</span></span>

<span data-ttu-id="d9049-231">Jeśli zawiesz, że możesz zobaczyć źródło tego samouczka [w naszym repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/).</span><span class="sxs-lookup"><span data-stu-id="d9049-231">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="d9049-232">Gratulacje, udało Ci się ukończyć wszystkie nasze wprowadzenie do samouczków języka C#.</span><span class="sxs-lookup"><span data-stu-id="d9049-232">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="d9049-233">Jeśli eager chcesz dowiedzieć się więcej, wypróbuj więcej naszych [samouczków](../index.md).</span><span class="sxs-lookup"><span data-stu-id="d9049-233">If you're eager to learn more, try more of our [tutorials](../index.md).</span></span>
