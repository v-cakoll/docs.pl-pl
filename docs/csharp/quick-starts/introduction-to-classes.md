---
title: "Przewodnik Szybki Start — wprowadzenie do klasy - C#"
description: "Utwórz pierwszy program C# i eksplorowanie obiektowej pojęcia"
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: ad6e83d427b55482f9615e0083682bdca6c56704
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="introduction-to-classes"></a><span data-ttu-id="0e127-103">Wprowadzenie do klas</span><span class="sxs-lookup"><span data-stu-id="0e127-103">Introduction to classes</span></span>

<span data-ttu-id="0e127-104">W tej lekcji założono, że po zainstalowaniu [.NET Core SDK](http://dot.net/core)i dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="0e127-104">This lesson assumes that you've installed [.NET Core SDK](http://dot.net/core), and an editor of your choice.</span></span> <span data-ttu-id="0e127-105">Jeśli nie masz, spróbuj [Visual Studio Code](https://code.visualstudio.com/), lub [programu Visual Studio](https://www.visualstudio.com/) na Mac lub Windows.</span><span class="sxs-lookup"><span data-stu-id="0e127-105">If you don't have one, try [Visual Studio Code](https://code.visualstudio.com/), or [Visual Studio](https://www.visualstudio.com/) on Mac or Windows.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="0e127-106">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="0e127-106">Create your application</span></span>

<span data-ttu-id="0e127-107">Przy użyciu okno terminalu, Utwórz katalog o nazwie **klasy**.</span><span class="sxs-lookup"><span data-stu-id="0e127-107">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="0e127-108">Aplikacja będzie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0e127-108">You'll build your application there.</span></span> <span data-ttu-id="0e127-109">Przejdź do tego katalogu i wpisz `dotnet new console` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="0e127-109">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="0e127-110">To polecenie tworzy aplikację.</span><span class="sxs-lookup"><span data-stu-id="0e127-110">This command creates your application.</span></span> <span data-ttu-id="0e127-111">Otwórz **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="0e127-111">Open **Program.cs**.</span></span> <span data-ttu-id="0e127-112">Go powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="0e127-112">It should look like this:</span></span>

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

<span data-ttu-id="0e127-113">W tym szybki start możesz zacząć tworzyć nowe typy, które reprezentują konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="0e127-113">In this quick start, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="0e127-114">Zwykle programiści określają każdej klasy w pliku tekstowym inny.</span><span class="sxs-lookup"><span data-stu-id="0e127-114">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="0e127-115">Który ułatwia zarządzanie wraz z rozwojem programu rozmiar.</span><span class="sxs-lookup"><span data-stu-id="0e127-115">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="0e127-116">Utwórz nowy plik o nazwie **BankAccount.cs** w **klasy** katalogu.</span><span class="sxs-lookup"><span data-stu-id="0e127-116">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="0e127-117">Ten plik będzie zawierać deefinition z ***konta bankowego***.</span><span class="sxs-lookup"><span data-stu-id="0e127-117">This file will contain the deefinition of a ***bank account***.</span></span> <span data-ttu-id="0e127-118">Obiekt programowania Oriented organizuje kodu przez tworzenie typów w formie ***klasy***.</span><span class="sxs-lookup"><span data-stu-id="0e127-118">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="0e127-119">Tych klas zawiera kod, który reprezentuje określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="0e127-119">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="0e127-120">`BankAccount` Klasa reprezentuje konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="0e127-120">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="0e127-121">Kod implementuje określonych operacji za pomocą metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e127-121">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="0e127-122">W tym szybki start konta bankowego obsługuje tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="0e127-122">In this quick start, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="0e127-123">Składa się z 10-cyfrowy numer, który unikatowo identyfikuje konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="0e127-123">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="0e127-124">Ma ona ciąg, który przechowuje nazwę lub nazwy właścicieli.</span><span class="sxs-lookup"><span data-stu-id="0e127-124">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="0e127-125">Saldo może zostać pobrany.</span><span class="sxs-lookup"><span data-stu-id="0e127-125">The balance can be retrieved.</span></span>
1. <span data-ttu-id="0e127-126">Akceptuje depozyty.</span><span class="sxs-lookup"><span data-stu-id="0e127-126">It accepts deposits.</span></span>
1. <span data-ttu-id="0e127-127">Akceptuje wycofanie.</span><span class="sxs-lookup"><span data-stu-id="0e127-127">It accepts withdrawals.</span></span>
1. <span data-ttu-id="0e127-128">Bilans początkowy musi być dodatnia.</span><span class="sxs-lookup"><span data-stu-id="0e127-128">The initial balance must be positive.</span></span>
1. <span data-ttu-id="0e127-129">Wycofanie nie może być ujemna równowagi.</span><span class="sxs-lookup"><span data-stu-id="0e127-129">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="0e127-130">Określ typ konta bankowego</span><span class="sxs-lookup"><span data-stu-id="0e127-130">Define the bank account type</span></span>

<span data-ttu-id="0e127-131">Można uruchomić tworzenia podstawy klasy definiującej tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="0e127-131">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="0e127-132">Go będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="0e127-132">It would look like this:</span></span>

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

        public void MakeWithdrawal(decimal amount, DateTime date, string payee, string note)
        {
        }
    }
}
```

<span data-ttu-id="0e127-133">Przed przejściem, Spójrzmy na został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="0e127-133">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="0e127-134">`namespace` Deklaracji umożliwia organizację kodu.</span><span class="sxs-lookup"><span data-stu-id="0e127-134">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="0e127-135">To szybki start jest stosunkowo mały, więc będzie umieścić cały kod w jednym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="0e127-135">This quick start is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="0e127-136">`public class BankAccount`definiuje klasę lub typ tworzony.</span><span class="sxs-lookup"><span data-stu-id="0e127-136">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="0e127-137">Wszystkie elementy wewnątrz `{` i `}` następujący klasy deklaracji definiuje zachowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="0e127-137">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="0e127-138">Istnieje pięć ***członków*** z `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="0e127-138">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="0e127-139">Pierwsze trzy są ***właściwości***.</span><span class="sxs-lookup"><span data-stu-id="0e127-139">The first three are ***properties***.</span></span> <span data-ttu-id="0e127-140">Właściwości elementów danych i może mieć kod, który wymusza sprawdzania poprawności lub inne zasady.</span><span class="sxs-lookup"><span data-stu-id="0e127-140">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="0e127-141">Ostatnie dwa są ***metody***.</span><span class="sxs-lookup"><span data-stu-id="0e127-141">The last two are ***methods***.</span></span> <span data-ttu-id="0e127-142">Metody są bloki kodu tego administracją jednej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0e127-142">Methods are blocks of code that peform a single function.</span></span> <span data-ttu-id="0e127-143">Odczytywanie nazwy wszystkich członków powinien podać informacji wystarczających lub innego projektanta zrozumieć, co oznacza klasy.</span><span class="sxs-lookup"><span data-stu-id="0e127-143">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="0e127-144">Otwórz nowe konto</span><span class="sxs-lookup"><span data-stu-id="0e127-144">Open a new account</span></span>

<span data-ttu-id="0e127-145">Pierwszy funkcja do wykonania jest otworzyć konto.</span><span class="sxs-lookup"><span data-stu-id="0e127-145">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="0e127-146">Gdy klient otworzy konto, musisz podać saldo początkowej oraz informacje o właściciela lub właścicieli tego konta.</span><span class="sxs-lookup"><span data-stu-id="0e127-146">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="0e127-147">Tworzenie nowego obiektu `BankAccount` typu, oznacza to zdefiniowanie ***Konstruktor*** który przypisuje tych wartości.</span><span class="sxs-lookup"><span data-stu-id="0e127-147">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="0e127-148">A ***konstruktora*** jest element członkowski, który ma taką samą nazwę jak klasa.</span><span class="sxs-lookup"><span data-stu-id="0e127-148">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="0e127-149">Służy do zainicjowania obiekty tego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="0e127-149">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="0e127-150">Dodaj następujący Konstruktor do `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="0e127-150">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="0e127-151">Konstruktory są wywoływane podczas tworzenia obiektów przy użyciu [ `new` ](../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="0e127-151">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="0e127-152">Zastąp linię `Console.WriteLine("Hello World!");` w ***program.cs*** o następujący wiersz (Zastąp `<name>` nazwą):</span><span class="sxs-lookup"><span data-stu-id="0e127-152">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="0e127-153">Typ `dotnet run` aby zobaczyć, co się stanie.</span><span class="sxs-lookup"><span data-stu-id="0e127-153">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="0e127-154">Zwróć uwagę, że numer konta jest puste?</span><span class="sxs-lookup"><span data-stu-id="0e127-154">Did you notice that the account number is blank?</span></span> <span data-ttu-id="0e127-155">Nadszedł czas, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="0e127-155">It's time to fix that.</span></span> <span data-ttu-id="0e127-156">Numer konta należy przydzielić podczas konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="0e127-156">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="0e127-157">Ale nie powinien być odpowiedzialność obiekt wywołujący, aby go utworzyć.</span><span class="sxs-lookup"><span data-stu-id="0e127-157">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="0e127-158">`BankAccount` Kod klasy wiedzieć, jak można przypisać nowe numery kont.</span><span class="sxs-lookup"><span data-stu-id="0e127-158">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="0e127-159">Prosty sposób, w tym celu ma rozpoczynać się od 10-cyfrowy numer.</span><span class="sxs-lookup"><span data-stu-id="0e127-159">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="0e127-160">Zwiększenia po utworzeniu każdego nowego konta.</span><span class="sxs-lookup"><span data-stu-id="0e127-160">Increment it when each new account is created.</span></span> <span data-ttu-id="0e127-161">Na koniec należy zapisać bieżący numer konta, gdy obiekt jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="0e127-161">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="0e127-162">Dodaj następujące deklaracji elementu członkowskiego do `BankAccount` klasy:</span><span class="sxs-lookup"><span data-stu-id="0e127-162">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="0e127-163">Jest to element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="0e127-163">This is a data member.</span></span> <span data-ttu-id="0e127-164">Ma ona `private`, co oznacza, że można uzyskać tylko przez kod wewnątrz `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="0e127-164">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="0e127-165">Jest to sposób rozdzielenia obowiązków publicznej (np. o numer konta) z prywatna implementacja (jak numery kont są generowane.) Dodaj następujące dwa wiersze do konstruktora, aby przypisać numer konta:</span><span class="sxs-lookup"><span data-stu-id="0e127-165">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="0e127-166">Typ `dotnet run` wyników.</span><span class="sxs-lookup"><span data-stu-id="0e127-166">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="0e127-167">Utwórz wpłat i wycofania</span><span class="sxs-lookup"><span data-stu-id="0e127-167">Create deposits and withdrawals</span></span>

<span data-ttu-id="0e127-168">Klasa konta bankowego musi zaakceptować wpłat i wycofania działała prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="0e127-168">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="0e127-169">Umożliwia wdrożenie wpłat i wycofania przez utworzenie dziennika dla każdej transakcji dla konta.</span><span class="sxs-lookup"><span data-stu-id="0e127-169">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="0e127-170">Który ma kilka zalet w porównaniu z po prostu aktualizowanie saldo każdą transakcję.</span><span class="sxs-lookup"><span data-stu-id="0e127-170">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="0e127-171">Historia może służyć do inspekcji wszystkich transakcji i zarządzanie nimi salda dzienne.</span><span class="sxs-lookup"><span data-stu-id="0e127-171">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="0e127-172">Przez obliczenie saldo z historii transakcji w razie potrzeby, wszelkie błędy w ramach jednej transakcji, które zostały usunięte zostaną poprawnie odzwierciedlone w Saldo na obliczenia dalej.</span><span class="sxs-lookup"><span data-stu-id="0e127-172">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="0e127-173">Zacznijmy od utworzenia nowego typu do reprezentowania transakcji.</span><span class="sxs-lookup"><span data-stu-id="0e127-173">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="0e127-174">To jest typem prostym, która nie ma żadnych obowiązki.</span><span class="sxs-lookup"><span data-stu-id="0e127-174">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="0e127-175">Musi on kilka właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e127-175">It needs a few properties.</span></span> <span data-ttu-id="0e127-176">Utwórz nowy plik o nazwie ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="0e127-176">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="0e127-177">Dodaj do niej następujący kod:</span><span class="sxs-lookup"><span data-stu-id="0e127-177">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="0e127-178">Teraz Dodajmy <xref:System.Collections.Generic.List%601> z `Transaction` obiekty do `BankAccount` klasy.</span><span class="sxs-lookup"><span data-stu-id="0e127-178">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="0e127-179">Dodaj następujące oświadczenie:</span><span class="sxs-lookup"><span data-stu-id="0e127-179">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="0e127-180"><xref:System.Collections.Generic.List%601> Klasy, musisz zaimportować inną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="0e127-180">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="0e127-181">Dodaj następujący kod na początku **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="0e127-181">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="0e127-182">Teraz Zmieńmy jak `Balance` został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="0e127-182">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="0e127-183">Można je znaleźć jako suma wartości wszystkich transakcji.</span><span class="sxs-lookup"><span data-stu-id="0e127-183">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="0e127-184">Modyfikowanie deklaracja `Balance` w `BankAccount` klasy do następującego:</span><span class="sxs-lookup"><span data-stu-id="0e127-184">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="0e127-185">W tym przykładzie pokazano ważnym aspektem ***właściwości***.</span><span class="sxs-lookup"><span data-stu-id="0e127-185">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="0e127-186">Saldo jest teraz wykrywanie, gdy inny programisty poprosi o podanie wartości.</span><span class="sxs-lookup"><span data-stu-id="0e127-186">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="0e127-187">Z obliczeń wylicza wszystkie transakcje i zapewnia Suma jako bieżące saldo.</span><span class="sxs-lookup"><span data-stu-id="0e127-187">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="0e127-188">Następnie należy zaimplementować `MakeDeposit` i `MakeWithdrawal` metody.</span><span class="sxs-lookup"><span data-stu-id="0e127-188">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="0e127-189">Tych metod będzie wymuszać końcowego dwie reguły: czy bilans początkowy musi być dodatnia i cofnięciu nie mogą tworzyć saldo ujemne.</span><span class="sxs-lookup"><span data-stu-id="0e127-189">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="0e127-190">To pojęcia związane z ***wyjątki***.</span><span class="sxs-lookup"><span data-stu-id="0e127-190">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="0e127-191">Standardowy sposób wskazujący, że metoda nie może pomyślnie wykonać pracę jest do zgłoszenia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0e127-191">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="0e127-192">Typ wyjątku i komunikat skojarzony z nim opis błędu.</span><span class="sxs-lookup"><span data-stu-id="0e127-192">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="0e127-193">W tym miejscu `MakeDeposit` metoda zgłasza wyjątek, jeśli ilość złożenia jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="0e127-193">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="0e127-194">`MakeWithdrawal` Metoda zgłasza wyjątek, jeśli kwota wycofania jest ujemny lub stosowania wycofanie powoduje saldo ujemne:</span><span class="sxs-lookup"><span data-stu-id="0e127-194">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="0e127-195">[ `throw` ](../language-reference/keywords/throw.md) Instrukcji **zgłasza** Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0e127-195">The [`throw`](../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="0e127-196">Kończy wykonywanie bieżącej metody i zostanie wznowiona, gdy odpowiadającego mu `catch` bloku został znaleziony.</span><span class="sxs-lookup"><span data-stu-id="0e127-196">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="0e127-197">Należy dodać `catch` blok do przetestowania tego kodu nieco później.</span><span class="sxs-lookup"><span data-stu-id="0e127-197">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="0e127-198">Konstruktora należy uzyskać jednej zmiany, dzięki czemu dodaje transakcję początkową, a nie bezpośrednio aktualizowanie saldo.</span><span class="sxs-lookup"><span data-stu-id="0e127-198">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="0e127-199">Ponieważ już zapisano `MakeDeposit` metody wywołać ją z sieci konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0e127-199">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="0e127-200">Zakończono Konstruktor powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="0e127-200">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="0e127-201"><xref:System.DateTime.Now?displayProperty=nameWithType>jest właściwością, która zwraca bieżącą datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="0e127-201"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="0e127-202">Testowania tej funkcji, dodając kilka wpłat i wycofywania w Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="0e127-202">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="0e127-203">Następnie testu, że są Przechwytywanie warunki błędów przez próby utworzenia konta z saldo ujemne:</span><span class="sxs-lookup"><span data-stu-id="0e127-203">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

```csharp
// Test that the initial balances must be positive:
try {
    var invalidAccount = new BankAccount("invalid", -55);
} catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="0e127-204">Możesz użyć [ `try` i `catch` instrukcje](../language-reference/keywords/try-catch.md) aby blok kodu, który może zgłaszać wyjątki i catch te błędy, które można spodziewać się.</span><span class="sxs-lookup"><span data-stu-id="0e127-204">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="0e127-205">Tę samą metodę można użyć do testowania kodu, która zgłasza salda ujemnego:</span><span class="sxs-lookup"><span data-stu-id="0e127-205">You can use the same technique to test the code that throws for a negative balance:</span></span>

```csharp
// Test for a negative balance
try {
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
} catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="0e127-206">Zapisz plik i typ `dotnet run` Wypróbuj ją.</span><span class="sxs-lookup"><span data-stu-id="0e127-206">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="0e127-207">Test — zalogować wszystkich transakcji</span><span class="sxs-lookup"><span data-stu-id="0e127-207">Challenge - log all transactions</span></span>

<span data-ttu-id="0e127-208">Aby zakończyć to szybki start, można napisać `GetAccountHistory` metodę, która tworzy `string` historii transakcji.</span><span class="sxs-lookup"><span data-stu-id="0e127-208">To finish this quick start, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="0e127-209">Dodaj tę metodę w celu `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="0e127-209">add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="0e127-210">Ta metoda korzysta <xref:System.Text.StringBuilder> klasy formatującej ciąg, który zawiera jeden wiersz dla każdej transakcji.</span><span class="sxs-lookup"><span data-stu-id="0e127-210">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="0e127-211">Przedstawiono ciągu formatowania kodu we wcześniejszej części tych Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="0e127-211">You've seen the string formatting code earlier in these quick starts.</span></span> <span data-ttu-id="0e127-212">Jest jeden znak nowego `\t`.</span><span class="sxs-lookup"><span data-stu-id="0e127-212">One new character is `\t`.</span></span> <span data-ttu-id="0e127-213">Która wstawia kartę, aby sformatować dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="0e127-213">That inserts a tab to format the output.</span></span>

<span data-ttu-id="0e127-214">Dodaj następujący wiersz do testowania w **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="0e127-214">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="0e127-215">Typ `dotnet run` wyników.</span><span class="sxs-lookup"><span data-stu-id="0e127-215">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0e127-216">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0e127-216">Next Steps</span></span>

<span data-ttu-id="0e127-217">Jeśli użytkownik został zablokowany, można wyświetlić źródła dla tego szybki start [w naszym repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="0e127-217">If you got stuck, you can see the source for this quick start [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="0e127-218">Gratulacje, po zakończeniu wszystkich naszych Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="0e127-218">Congratulations, you've finished all our Quick Starts.</span></span> <span data-ttu-id="0e127-219">Jeśli chcesz dowiedzieć się więcej, spróbuj naszych [samouczki](../tutorials/index.md)</span><span class="sxs-lookup"><span data-stu-id="0e127-219">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>
