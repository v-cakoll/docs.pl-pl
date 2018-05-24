---
title: Samouczek interpolacji ciągu - C# lokalnego poradniki Szybki Start
description: Ta opcja szybkiego startu przedstawia zawiera wyrażenie sformatowane wyniki w większych ciągu przy użyciu funkcji interpolacji ciągu języka C#.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: a4e8434b3e7f945ad002984ad7861c0e103c0cf2
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="string-interpolation"></a><span data-ttu-id="2d2b7-103">Ciąg interpolacji</span><span class="sxs-lookup"><span data-stu-id="2d2b7-103">String interpolation</span></span>

<span data-ttu-id="2d2b7-104">Ta opcja szybkiego startu zawiera wskazówki, jak używać języka C# [ciągu interpolacji](../language-reference/tokens/interpolated.md) do wstawienia wartości na ciąg pojedynczego wyniku.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-104">This quickstart teaches you how to use C# [string interpolation](../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="2d2b7-105">Pisanie kodu C# i wyświetlić wyniki kompilowania i uruchamiania go.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="2d2b7-106">Procedury szybkiego startu zawiera szereg lekcje, które pokazują, jak wstawienia wartości do ciągu i sformatować te wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-106">The quickstart contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="2d2b7-107">Ta opcja szybkiego startu oczekuje, że maszynie, która służy do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="2d2b7-108">Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="2d2b7-109">Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego poradniki Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> <span data-ttu-id="2d2b7-110">Można też wykonać [wersji interaktywnego](interpolated-strings.yml) z tego przewodnika Szybki Start w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-110">You also can complete the [interactive version](interpolated-strings.yml) of this quickstart in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="2d2b7-111">Tworzenie ciągu interpolowanym</span><span class="sxs-lookup"><span data-stu-id="2d2b7-111">Create an interpolated string</span></span>

<span data-ttu-id="2d2b7-112">Utwórz katalog o nazwie **interpolowane**.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-112">Create a directory named **interpolated**.</span></span> <span data-ttu-id="2d2b7-113">Stał się bieżący katalog i uruchom następujące polecenie z poziomu okna konsoli:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-113">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="2d2b7-114">To polecenie tworzy nową aplikację konsolową .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="2d2b7-115">Otwórz **Program.cs** ulubionego edytora i Zastąp linię `Console.WriteLine("Hello World!");` z następującym kodem, gdzie Zastąp `<name>` nazwą:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="2d2b7-116">Spróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="2d2b7-117">Po uruchomieniu program wyświetla jeden ciąg zawierający nazwę w pozdrowienie.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-117">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="2d2b7-118">Ciąg zawarty w <xref:System.Console.WriteLine%2A> jest wywołanie metody *interpolowane ciąg*.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-118">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="2d2b7-119">Jest to rodzaj szablonu, który pozwala utworzyć jeden ciąg (o nazwie *powoduje ciąg*) z ciągu, który zawiera osadzony kod.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-119">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="2d2b7-120">Ciągi interpolowane są szczególnie użyteczne w przypadku wstawiania wartości w ciągu lub ciągi łączenie (łączenie).</span><span class="sxs-lookup"><span data-stu-id="2d2b7-120">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="2d2b7-121">Ten prosty przykład zawiera dwa elementy, które muszą mieć co ciągu interpolowanym:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-121">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="2d2b7-122">Literał ciągu rozpoczynający się od `$` znak przed jego otwierania przez cudzysłów znaków.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-122">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="2d2b7-123">Nie może być odstępów między `$` symboli i znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-123">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="2d2b7-124">(Jeśli chcesz zobaczyć co się stanie w przypadku obejmują jeden, Wstaw spację po `$` znak, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-124">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="2d2b7-125">Kompilator języka C# Wyświetla komunikat o błędzie "Błąd CS1056: nieoczekiwany znak"$"".)</span><span class="sxs-lookup"><span data-stu-id="2d2b7-125">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="2d2b7-126">Co najmniej jeden *interpolowane wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-126">One or more *interpolated expressions*.</span></span> <span data-ttu-id="2d2b7-127">Wskazuje wyrażenie interpolowane otwierający i zamykający nawias klamrowy (`{` i `}`).</span><span class="sxs-lookup"><span data-stu-id="2d2b7-127">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="2d2b7-128">Możesz też zaznaczyć dowolne C# wyrażenie zwracające wartość (w tym `null`) w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-128">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="2d2b7-129">Poniżej przedstawiono kilka innych przykładów interpolacji ciągu z innych typów danych.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-129">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="2d2b7-130">Obejmują różne typy danych</span><span class="sxs-lookup"><span data-stu-id="2d2b7-130">Include different data types</span></span>

<span data-ttu-id="2d2b7-131">W poprzedniej sekcji interpolacji ciąg jest używany do wstawiania jeden ciąg wewnątrz innego.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-131">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="2d2b7-132">Wynik wyrażenia interpolowane może być jednak każdego typu danych.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-132">The result of an interpolated expression can be of any data type, though.</span></span> <span data-ttu-id="2d2b7-133">Załóżmy obejmują wartości różnych typów danych w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-133">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="2d2b7-134">W poniższym przykładzie najpierw definiujemy [klasy](../programming-guide/classes-and-structs/classes.md) — typ danych `Vegetable` mający `Name` [właściwości](../properties.md) i `ToString` [metody](../methods.md), która [zastępuje](../language-reference/keywords/override.md) zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-134">In the following example, first, we define a [class](../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has the `Name` [property](../properties.md) and the `ToString` [method](../methods.md), which [overrides](../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2d2b7-135">[ `public` Modyfikator dostępu](../language-reference/keywords/public.md) udostępnia tej metody do dowolnego kod klienta w celu uzyskania reprezentację ciągu `Vegetable` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-135">The [`public` access modifier](../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="2d2b7-136">W przykładzie `Vegetable.ToString` metoda zwraca wartość `Name` właściwość, która została zainicjowana w `Vegetable` [konstruktora](../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="2d2b7-136">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="2d2b7-137">Następnie utwórz wystąpienie `Vegetable` przy użyciu [ `new` — słowo kluczowe](../language-reference/keywords/new-operator.md) i podając nazwę parametru konstruktora `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-137">Then we create an instance of the `Vegetable` class by using [`new` keyword](../language-reference/keywords/new-operator.md) and providing a name parameter for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="2d2b7-138">Na koniec przeprowadzamy `item` zmiennej w ciągu interpolowanym zawierającej również <xref:System.DateTime> wartość, <xref:System.Decimal> wartości i `Unit` [wyliczenie](../programming-guide/enumeration-types.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-138">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="2d2b7-139">Zamień wszystkie kodu C# w Edytorze następujący kod, a następnie użyj `dotnet run` polecenie, aby uruchomić go:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-139">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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
   public enum Unit { item, pound, ounce, dozen };

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

<span data-ttu-id="2d2b7-140">Należy pamiętać, że interpolowanego wyrażenia `item` w ciągu interpolowanym jest rozpoznawana jako tekst "oberżynowego" w ciągu wynik.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-140">Note that the interpolated expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="2d2b7-141">Wynika to, gdy typ wyniku wyrażenia nie jest ciągiem, wynik został rozwiązany na ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-141">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="2d2b7-142">Jeśli interpolowanego wyrażenia `null`, ciąg pusty ("", lub <xref:System.String.Empty?displayProperty=nameWithType>) jest używany.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-142">If the interpolated expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="2d2b7-143">Jeśli interpolowanego wyrażenia nie być `null`, zwykle `ToString` wywoływana jest metoda typu wyniku.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-143">If the interpolated expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="2d2b7-144">Można to sprawdzić, aktualizując wykonania `Vegetable.ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-144">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="2d2b7-145">Być może nawet nie implementuje `ToString` metody, ponieważ niektóre implementacja tej metody ma wszystkie typy danych języka C#.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-145">You might even not implement `ToString` method since every C# data type has some implementation of this method.</span></span> <span data-ttu-id="2d2b7-146">Aby sprawdzić, czy, w komentarz definicję `Vegetable.ToString` metody w tym przykładzie (w tym celu umieść symbol komentarza `//` przed nim).</span><span class="sxs-lookup"><span data-stu-id="2d2b7-146">To test that, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol `//` in front of it).</span></span> <span data-ttu-id="2d2b7-147">W danych wyjściowych, ciąg "oberżynowego" zostanie zastąpiony przez w pełni kwalifikowaną nazwę typu ("roślinny" w tym przykładzie), który jest domyślnym zachowaniem z <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-147">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2d2b7-148">Domyślne zachowanie `ToString` metody dla typu wyliczenia jest zwraca reprezentację ciągu wartość używana w definicji wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-148">Default behavior of the `ToString` method for an enumeration type is to return the string representation of a value used at the definition of the enumeration.</span></span>

<span data-ttu-id="2d2b7-149">W danych wyjściowych w tym przykładzie Data jest zbyt precyzyjna (cena oberżynowego nie zmienia co sekundę), a wartość ceny nie oznacza jednostkę waluty.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-149">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="2d2b7-150">W następnej sekcji dowiesz się, jak rozwiązać te problemy kontrolując formatu ciągu reprezentacje wyników wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-150">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="2d2b7-151">Formant formatowanie interpolowanego wyrażenia</span><span class="sxs-lookup"><span data-stu-id="2d2b7-151">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="2d2b7-152">W poprzedniej sekcji nieprawidłowo sformatowany dwa ciągi, które zostały wstawione do ciągu wynik.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-152">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="2d2b7-153">Jeden jest wartość daty i godziny, dla którego został właściwe tylko data.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-153">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="2d2b7-154">Drugi był cenę nie wskazywać jego jednostkę waluty.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-154">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="2d2b7-155">Problemy z obu łatwych do adresu.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-155">Both issues are easy to address.</span></span> <span data-ttu-id="2d2b7-156">Ciąg interpolacji umożliwia określenie *ciągi formatujące* umożliwiające sterowanie formatowanie poszczególnych typów.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-156">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="2d2b7-157">Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby uwzględnić ciągi formatujące datę i cenę wyrażeń, jak pokazano w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-157">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="2d2b7-158">Podaj ciąg formatu, używając interpolowanego wyrażenia dwukropka (":"), a ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-158">You specify a format string by following the interpolated expression with a colon (":") and the format string.</span></span> <span data-ttu-id="2d2b7-159">"d" jest [standardowa Data i godzina ciąg formatu](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) reprezentujący format daty krótkiej.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-159">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="2d2b7-160">"C2" jest [ciągu standardowego formatu liczbowego](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) reprezentujący liczbę jako wartość walutową z dwóch cyfr po punkcie dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-160">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="2d2b7-161">Liczba typów w bibliotek .NET obsługuje zestaw wstępnie zdefiniowanych ciągi formatów.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-161">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="2d2b7-162">Obejmuje to wszystkie typy liczbowe oraz typy daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-162">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="2d2b7-163">Pełną listę typów, które obsługują ciągi formatów, zobacz [ciągi formatów i typy biblioteki klas .NET](../../standard/base-types/formatting-types.md#stringRef) w [typy formatowania w .NET](../../standard/base-types/formatting-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-163">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="2d2b7-164">Spróbuj zmodyfikować ciągów formatu w edytorze tekstu i, za każdym razem, wprowadzić zmiany, ponownie uruchom program, aby zobaczyć wpływ zmian na format daty i godziny oraz wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-164">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="2d2b7-165">Zmiana "d" `{date:d}` "t" (do wyświetlania na format godziny krótkiej), "y" (Aby wyświetlić rok i miesiąc), a "yyyy" (do wyświetlania roku w postaci czterech cyfr).</span><span class="sxs-lookup"><span data-stu-id="2d2b7-165">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="2d2b7-166">Zmiana "C2" `{price:C2}` "e" (w notacji wykładniczej) i "F3" (dla wartość liczbową z trzech cyfr po punkcie dziesiętnym).</span><span class="sxs-lookup"><span data-stu-id="2d2b7-166">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="2d2b7-167">Oprócz kontrolowanie formatowania, można też kontrolować szerokość pola i wyrównanie sformatowany ciągów, które znajdują się w ciągu wynik.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-167">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="2d2b7-168">W następnej sekcji dowiesz się, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-168">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="2d2b7-169">Szerokość pola i wyrównanie interpolowanego wyrażenia</span><span class="sxs-lookup"><span data-stu-id="2d2b7-169">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="2d2b7-170">Zwykle podczas formatowania wynik wyrażenia interpolowane na ciąg, ten ciąg znajduje się w ciągu wynik bez początkowe lub końcowe spacje.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-170">Ordinarily, when the result of an interpolated expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="2d2b7-171">Szczególnie podczas pracy z zestawem danych, możliwość kontrolowania szerokość pola i pomaga wyrównanie tekstu, aby wygenerować bardziej czytelny dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-171">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="2d2b7-172">Aby wyświetlić to Zastąp następujący kod całego kodu w edytorze tekstu, następnie wpisz `dotnet run` do wykonania programu:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-172">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="2d2b7-173">Nazwy autorów są wyrównane do lewej, a tytułów, które są napisane są wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-173">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="2d2b7-174">Określ wyrównanie przez dodanie przecinka (",") po interpolowanego wyrażenia i wyznaczające *minimalna* szerokości pola.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-174">You specify the alignment by adding a comma (",") after an interpolated expression and designating the *minimum* field width.</span></span> <span data-ttu-id="2d2b7-175">Jeśli określona wartość jest liczbą dodatnią, to pole jest wyrównany do prawej.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-175">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="2d2b7-176">Jeśli jest liczbą ujemną, to pole jest wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-176">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="2d2b7-177">Spróbuj usunąć ujemna znaki z `{"Author",-25}` i `{title.Key,-25}` kodu i ponownie uruchomić przykład, tak jak w następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-177">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="2d2b7-178">Teraz, informacje o autorze jest wyrównany do prawej.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-178">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="2d2b7-179">Specyfikator wyrównania i ciągu formatu dla pojedynczego wyrażenia interpolowane można łączyć.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-179">You can combine an alignment specifier and a format string for a single interpolated expression.</span></span> <span data-ttu-id="2d2b7-180">W tym celu Określ wyrównanie najpierw następuje dwukropek i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-180">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="2d2b7-181">Zamień wszystkie kodu wewnątrz `Main` metodę z następującym kodem, która zawiera trzy ciągi sformatowane z zdefiniowane szerokości pól.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-181">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="2d2b7-182">Następnie uruchom program wprowadzając `dotnet run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-182">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="2d2b7-183">Dane wyjściowe podobne następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2d2b7-183">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="2d2b7-184">Zakończono szybkiego startu interpolacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-184">You've completed the string interpolation quickstart.</span></span>

<span data-ttu-id="2d2b7-185">Można kontynuować [listy kolekcji](arrays-and-collections.md) szybkiego startu w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-185">You can continue with the [List collection](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="2d2b7-186">Aby uzyskać więcej informacji, zobacz [ciągu interpolacji](../language-reference/tokens/interpolated.md) tematu i [ciągu interpolacji w języku C#](../tutorials/string-interpolation.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="2d2b7-186">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>
