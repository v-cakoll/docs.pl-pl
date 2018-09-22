---
title: Samouczek interpolacji ciągu — C# lokalnego przewodników Szybki Start
description: Ten przewodnik Szybki Start przedstawia sposób użycia funkcji interpolacji ciągu C# do uwzględnienia wyrażenie sformatowane wyniki w dłuższym ciągu.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: da111790ebbc299df16297650347045b9395a90f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580697"
---
# <a name="string-interpolation"></a><span data-ttu-id="e720e-103">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="e720e-103">String interpolation</span></span>

<span data-ttu-id="e720e-104">Ten przewodnik Szybki Start pokazano, jak używać języka C# [Interpolacja ciągów](../language-reference/tokens/interpolated.md) wstawiania wartości do ciągu pojedynczego wyniku.</span><span class="sxs-lookup"><span data-stu-id="e720e-104">This quickstart teaches you how to use C# [string interpolation](../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="e720e-105">Możesz pisać kod w języku C# i zobaczyć wyniki kompilowania i uruchamiania ich.</span><span class="sxs-lookup"><span data-stu-id="e720e-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="e720e-106">Samouczek Szybki Start zawiera serię lekcji, które przedstawiają sposób wstawiania wartości do ciągów i formatują te wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="e720e-106">The quickstart contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="e720e-107">Ten przewodnik Szybki Start oczekuje, że masz maszyny, których można użyć do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e720e-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="e720e-108">Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux.</span><span class="sxs-lookup"><span data-stu-id="e720e-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="e720e-109">Krótkie omówienie poleceń użyjesz znajduje się w [wprowadzenie do lokalnego przewodników Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="e720e-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> <span data-ttu-id="e720e-110">Można też wykonać [interaktywne wersji](interpolated-strings.yml) tego przewodnika Szybki Start w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="e720e-110">You also can complete the [interactive version](interpolated-strings.yml) of this quickstart in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="e720e-111">Tworzenie ciągu interpolowanego</span><span class="sxs-lookup"><span data-stu-id="e720e-111">Create an interpolated string</span></span>

<span data-ttu-id="e720e-112">Utwórz katalog o nazwie **interpolowane**.</span><span class="sxs-lookup"><span data-stu-id="e720e-112">Create a directory named **interpolated**.</span></span> <span data-ttu-id="e720e-113">Przekształcić ją w bieżącym katalogu i uruchom następujące polecenie z okna konsoli:</span><span class="sxs-lookup"><span data-stu-id="e720e-113">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="e720e-114">To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e720e-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="e720e-115">Otwórz **Program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem, gdzie możesz zastąpić `<name>` z Twoją nazwą:</span><span class="sxs-lookup"><span data-stu-id="e720e-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="e720e-116">Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e720e-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="e720e-117">Kiedy uruchamiasz program, wyświetla pojedynczy ciąg, z Twoim imieniem w powitaniu.</span><span class="sxs-lookup"><span data-stu-id="e720e-117">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="e720e-118">Ciąg umieszczony w <xref:System.Console.WriteLine%2A> jest wywołanie metody *ciągiem interpolowanym*.</span><span class="sxs-lookup"><span data-stu-id="e720e-118">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="e720e-119">Jest to rodzaj szablonu, który umożliwia skonstruowanie pojedynczego ciągu (o nazwie *ciągiem wynikowym*) z ciągu obejmującego osadzony kod.</span><span class="sxs-lookup"><span data-stu-id="e720e-119">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="e720e-120">Ciągi interpolowane są szczególnie użyteczne do wstawiania wartości do ciągu lub łączenia (łączenie) ciągów.</span><span class="sxs-lookup"><span data-stu-id="e720e-120">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="e720e-121">Ten prosty przykład zawiera dwa elementy, które muszą mieć każdy ciąg interpolowany:</span><span class="sxs-lookup"><span data-stu-id="e720e-121">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="e720e-122">Literał ciągu rozpoczynający się od `$` znak przed jego otwierającym znakiem cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="e720e-122">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="e720e-123">Nie może być spacji między `$` symboli i znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="e720e-123">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="e720e-124">(Jeśli chcesz zobaczyć, co się stanie po wstawieniu odstępu, Wstaw go po `$` znak, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e720e-124">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="e720e-125">Kompilator języka C#, wyświetla komunikat o błędzie "Błąd CS1056: nieoczekiwany znak '$'".)</span><span class="sxs-lookup"><span data-stu-id="e720e-125">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="e720e-126">Co najmniej jeden *wyrażeń interpolowanych*.</span><span class="sxs-lookup"><span data-stu-id="e720e-126">One or more *interpolated expressions*.</span></span> <span data-ttu-id="e720e-127">Wyrażenie interpolowane jest wskazywane przez nawias klamrowy otwierający i zamykający (`{` i `}`).</span><span class="sxs-lookup"><span data-stu-id="e720e-127">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="e720e-128">Możesz umieścić dowolne C# wyrażenie zwracające wartość (w tym `null`) wewnątrz nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="e720e-128">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="e720e-129">Wypróbujmy kilka dodatkowych przykładowych interpolacji ciągu z innymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="e720e-129">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="e720e-130">Uwzględnianie innych typów danych</span><span class="sxs-lookup"><span data-stu-id="e720e-130">Include different data types</span></span>

<span data-ttu-id="e720e-131">W poprzedniej sekcji Interpolacja ciągów jest używany do wstawienia jednego ciągu wewnątrz innego.</span><span class="sxs-lookup"><span data-stu-id="e720e-131">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="e720e-132">Wynik wyrażenia interpolowanego może być dowolnego typu danych, mimo że.</span><span class="sxs-lookup"><span data-stu-id="e720e-132">The result of an interpolated expression can be of any data type, though.</span></span> <span data-ttu-id="e720e-133">Teraz zawierać wartości różnych typów danych w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="e720e-133">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="e720e-134">W poniższym przykładzie najpierw definiujemy [klasy](../programming-guide/classes-and-structs/classes.md) — typ danych `Vegetable` zawierający `Name` [właściwość](../properties.md) i `ToString` [metoda](../methods.md), który [zastępuje](../language-reference/keywords/override.md) zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e720e-134">In the following example, first, we define a [class](../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has the `Name` [property](../properties.md) and the `ToString` [method](../methods.md), which [overrides](../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e720e-135">[ `public` Modyfikator dostępu](../language-reference/keywords/public.md) sprawia, że tej metody jest dostępny dla dowolnego kodu klienta, można pobrać reprezentacji w postaci ciągu `Vegetable` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e720e-135">The [`public` access modifier](../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="e720e-136">W przykładzie `Vegetable.ToString` metoda zwraca wartość `Name` właściwości, który jest inicjowany w `Vegetable` [Konstruktor](../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="e720e-136">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="e720e-137">Następnie tworzymy wystąpienie `Vegetable` przy użyciu [ `new` — słowo kluczowe](../language-reference/keywords/new-operator.md) i podając parametr name dla konstruktora `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="e720e-137">Then we create an instance of the `Vegetable` class by using [`new` keyword](../language-reference/keywords/new-operator.md) and providing a name parameter for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="e720e-138">Na koniec dołączamy `item` zmiennej do ciągu interpolowanego, który zawiera także <xref:System.DateTime> wartość <xref:System.Decimal> wartości i `Unit` [wyliczenie](../programming-guide/enumeration-types.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="e720e-138">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="e720e-139">Zastąp cały kod C# w edytorze następującym kodem, a następnie użyj `dotnet run` polecenie, aby go uruchomić:</span><span class="sxs-lookup"><span data-stu-id="e720e-139">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, kilogram, gram, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

<span data-ttu-id="e720e-140">Należy pamiętać, że wyrażenie interpolowane `item` w ciągu interpolowanym jest rozpoznawany jako tekst "eggplant" w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="e720e-140">Note that the interpolated expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="e720e-141">To dlatego, gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest tłumaczona na ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e720e-141">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="e720e-142">Jeśli wyrażenie interpolowane daje w wyniku `null`, ciąg pusty ("", lub <xref:System.String.Empty?displayProperty=nameWithType>) jest używany.</span><span class="sxs-lookup"><span data-stu-id="e720e-142">If the interpolated expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="e720e-143">Jeśli wyrażenie interpolowane nie mają `null`, zazwyczaj `ToString` zostanie wywołana metoda typ wyniku.</span><span class="sxs-lookup"><span data-stu-id="e720e-143">If the interpolated expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="e720e-144">Można to sprawdzić, aktualizując wykonania `Vegetable.ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="e720e-144">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="e720e-145">Może nawet trzeba zaimplementować `ToString` metody, ponieważ każdy typ ma pewne implementacja tej metody.</span><span class="sxs-lookup"><span data-stu-id="e720e-145">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="e720e-146">Aby to przetestować, przekształcić w komentarz definicję `Vegetable.ToString` metody w przykładzie (w tym celu należy umieścić symbol komentarza `//`, przed nim).</span><span class="sxs-lookup"><span data-stu-id="e720e-146">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="e720e-147">W danych wyjściowych ciąg "eggplant" został zastąpiony w pełni kwalifikowana nazwa typu ("roślinnego" w tym przykładzie), który jest domyślnym zachowaniem z <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e720e-147">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e720e-148">Domyślne zachowanie `ToString` metodą wartość wyliczenia jest zwraca reprezentację ciągu wartości.</span><span class="sxs-lookup"><span data-stu-id="e720e-148">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="e720e-149">W danych wyjściowych z tego przykładu Data jest zbyt precyzyjna (cena eggplant nie zmienia się każda sekunda), a wartość ceny nie wskazuje jednostkę waluty.</span><span class="sxs-lookup"><span data-stu-id="e720e-149">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="e720e-150">W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format ciągów reprezentujących wyniki wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e720e-150">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="e720e-151">Kontrolowanie formatowania wyrażeń interpolowanych</span><span class="sxs-lookup"><span data-stu-id="e720e-151">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="e720e-152">W poprzedniej sekcji dwa nie najlepiej sformatowane ciągi zostały wstawione do ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="e720e-152">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="e720e-153">Jedna była wartość daty i godziny, dla którego tylko data powinna mieć zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="e720e-153">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="e720e-154">Drugim była cena, która nie wskazywała waluty.</span><span class="sxs-lookup"><span data-stu-id="e720e-154">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="e720e-155">Zarówno w przypadku problemów są łatwe do adresu.</span><span class="sxs-lookup"><span data-stu-id="e720e-155">Both issues are easy to address.</span></span> <span data-ttu-id="e720e-156">Interpolacja ciągów pozwala określić *ciągi formatujące* które kontrolują formatowanie poszczególnych typów.</span><span class="sxs-lookup"><span data-stu-id="e720e-156">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="e720e-157">Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby dołączyć ciągi formatu daty i ceny wyrażeń, jak pokazano w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="e720e-157">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="e720e-158">Należy określić ciąg formatu, postępując zgodnie z wyrażenia interpolowanego z dwukropkiem (":") i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="e720e-158">You specify a format string by following the interpolated expression with a colon (":") and the format string.</span></span> <span data-ttu-id="e720e-159">"d" jest [ciąg formatu standardowego daty i godziny](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) reprezentujący formatu daty krótkiej.</span><span class="sxs-lookup"><span data-stu-id="e720e-159">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="e720e-160">"C2" to [standardowy Ciąg formatujący](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) reprezentujący liczbę jako wartość waluty z dwoma cyframi po separatorze dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="e720e-160">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="e720e-161">Liczba typów w bibliotekach .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatu.</span><span class="sxs-lookup"><span data-stu-id="e720e-161">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="e720e-162">Dotyczy to wszystkich typów liczbowych i typów daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="e720e-162">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="e720e-163">Aby uzyskać pełną listę typów, które obsługują ciągi formatu, zobacz [ciągi formatu i typy biblioteki klas .NET](../../standard/base-types/formatting-types.md#stringRef) w [typy formatowania na platformie .NET](../../standard/base-types/formatting-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="e720e-163">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="e720e-164">Spróbuj zmodyfikować ciągi formatu w edytorze tekstu i, za każdym razem, wprowadzić zmiany, ponownie uruchom program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="e720e-164">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="e720e-165">Zmień "d" w `{date:d}` na "t" (Aby wyświetlić krótki format daty), "y" (Aby wyświetlić rok i miesiąc) oraz "yyyy" (Aby wyświetlać rok jako liczbę czterocyfrową).</span><span class="sxs-lookup"><span data-stu-id="e720e-165">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="e720e-166">Zmień "C2" w `{price:C2}` "e" (notacja wykładnicza) oraz "F3" (wartość liczbową z trzema cyframi po separatorze dziesiętnym).</span><span class="sxs-lookup"><span data-stu-id="e720e-166">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="e720e-167">Poza kontrolowaniem formatowania możesz też kontrolować szerokość pola i wyrównanie sformatowanego ciągów, które znajdują się w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="e720e-167">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="e720e-168">W następnej sekcji dowiesz się, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="e720e-168">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="e720e-169">Kontrolowanie szerokości pola i wyrównania wyrażeń interpolowanych</span><span class="sxs-lookup"><span data-stu-id="e720e-169">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="e720e-170">Zazwyczaj gdy wynikiem wyrażenia interpolowane jest sformatowany ciąg, ciąg znajduje się w ciągu wynikowym bez spacji wiodących albo końcowych.</span><span class="sxs-lookup"><span data-stu-id="e720e-170">Ordinarily, when the result of an interpolated expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="e720e-171">Szczególnie podczas pracy z zestawem danych, można kontrolować szerokość pola i wyrównanie tekstu pozwala tworzyć bardziej czytelny dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e720e-171">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="e720e-172">Aby to zobaczyć, Zastąp cały kod w edytorze tekstu z następującym kodem, a następnie wpisz `dotnet run` do wykonania programu:</span><span class="sxs-lookup"><span data-stu-id="e720e-172">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

<span data-ttu-id="e720e-173">Nazwy autorzy są wyrównane do lewej, a tytułów, które one napisane są wyrównane do prawej.</span><span class="sxs-lookup"><span data-stu-id="e720e-173">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="e720e-174">Wyrównanie określa się poprzez dodanie przecinka (",") po wyrażenie interpolowane i wyznaczające *minimalne* szerokości pola.</span><span class="sxs-lookup"><span data-stu-id="e720e-174">You specify the alignment by adding a comma (",") after an interpolated expression and designating the *minimum* field width.</span></span> <span data-ttu-id="e720e-175">Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównany do prawej.</span><span class="sxs-lookup"><span data-stu-id="e720e-175">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="e720e-176">Jeśli jest liczbą ujemną, pole jest wyrównany do lewej.</span><span class="sxs-lookup"><span data-stu-id="e720e-176">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="e720e-177">Spróbuj usunąć znaki ujemne z `{"Author",-25}` i `{title.Key,-25}` kodu i uruchomić przykładowy kod ponownie, tak jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e720e-177">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="e720e-178">Ten czas, informacje o autorze jest wyrównany do prawej.</span><span class="sxs-lookup"><span data-stu-id="e720e-178">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="e720e-179">Możesz połączyć specyfikator wyrównania i ciąg formatu dla pojedynczego wyrażenia interpolowane.</span><span class="sxs-lookup"><span data-stu-id="e720e-179">You can combine an alignment specifier and a format string for a single interpolated expression.</span></span> <span data-ttu-id="e720e-180">Aby to zrobić, określ wyrównanie najpierw następuje dwukropek i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="e720e-180">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="e720e-181">Zastąp cały kod wewnątrz `Main` metoda następującym kodem, który wyświetla trzy sformatowane ciągi ze zdefiniowanych szerokościami pól.</span><span class="sxs-lookup"><span data-stu-id="e720e-181">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="e720e-182">Następnie uruchom program, wprowadzając `dotnet run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="e720e-182">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="e720e-183">Dane wyjściowe wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="e720e-183">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="e720e-184">Ukończono Szybki Start interpolacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="e720e-184">You've completed the string interpolation quickstart.</span></span>

<span data-ttu-id="e720e-185">Możesz kontynuować [listy kolekcji](arrays-and-collections.md) Szybki Start w środowisku projektowym.</span><span class="sxs-lookup"><span data-stu-id="e720e-185">You can continue with the [List collection](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="e720e-186">Aby uzyskać więcej informacji, zobacz [Interpolacja ciągów](../language-reference/tokens/interpolated.md) tematu i [Interpolacja w języku C# ciągów](../tutorials/string-interpolation.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="e720e-186">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>
