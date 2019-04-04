---
title: Interpolacja - ciągów C# samouczek
description: W tym samouczku dowiesz się, jak używać C# funkcji interpolacji ciągów, aby uwzględnić wyrażenie sformatowane wyniki w dłuższym ciągu.
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: 97773659ea7dd00c291aa6a96401cac531adfdc8
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921452"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="661b5-103">Konstruowania sformatowane ciągi za pomocą Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="661b5-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="661b5-104">W tym samouczku pokazano sposób użycia C# [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) wstawiania wartości do ciągu pojedynczego wyniku.</span><span class="sxs-lookup"><span data-stu-id="661b5-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="661b5-105">Możesz pisać kod w języku C# i zobaczyć wyniki kompilowania i uruchamiania ich.</span><span class="sxs-lookup"><span data-stu-id="661b5-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="661b5-106">Samouczek zawiera serię lekcji, które przedstawiają sposób wstawiania wartości do ciągów i formatują te wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="661b5-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="661b5-107">W tym samouczku oczekuje, że masz maszyny, których można użyć do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="661b5-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="661b5-108">Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux.</span><span class="sxs-lookup"><span data-stu-id="661b5-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="661b5-109">Można też wykonać [interaktywne wersji](interpolated-strings.yml) po ukończeniu tego samouczka w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="661b5-109">You also can complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="661b5-110">Tworzenie ciągu interpolowanego</span><span class="sxs-lookup"><span data-stu-id="661b5-110">Create an interpolated string</span></span>

<span data-ttu-id="661b5-111">Utwórz katalog o nazwie **interpolowane**.</span><span class="sxs-lookup"><span data-stu-id="661b5-111">Create a directory named **interpolated**.</span></span> <span data-ttu-id="661b5-112">Przekształcić ją w bieżącym katalogu i uruchom następujące polecenie z okna konsoli:</span><span class="sxs-lookup"><span data-stu-id="661b5-112">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="661b5-113">To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="661b5-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="661b5-114">Otwórz **Program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem, gdzie możesz zastąpić `<name>` z Twoją nazwą:</span><span class="sxs-lookup"><span data-stu-id="661b5-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="661b5-115">Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="661b5-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="661b5-116">Kiedy uruchamiasz program, wyświetla pojedynczy ciąg, z Twoim imieniem w powitaniu.</span><span class="sxs-lookup"><span data-stu-id="661b5-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="661b5-117">Ciąg umieszczony w <xref:System.Console.WriteLine%2A> jest wywołanie metody *ciągiem interpolowanym*.</span><span class="sxs-lookup"><span data-stu-id="661b5-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="661b5-118">Jest to rodzaj szablonu, który umożliwia skonstruowanie pojedynczego ciągu (o nazwie *ciągiem wynikowym*) z ciągu obejmującego osadzony kod.</span><span class="sxs-lookup"><span data-stu-id="661b5-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="661b5-119">Ciągi interpolowane są szczególnie użyteczne do wstawiania wartości do ciągu lub łączenia (łączenie) ciągów.</span><span class="sxs-lookup"><span data-stu-id="661b5-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="661b5-120">Ten prosty przykład zawiera dwa elementy, które muszą mieć każdy ciąg interpolowany:</span><span class="sxs-lookup"><span data-stu-id="661b5-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="661b5-121">Literał ciągu rozpoczynający się od `$` znak przed jego otwierającym znakiem cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="661b5-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="661b5-122">Nie może być spacji między `$` symboli i znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="661b5-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="661b5-123">(Jeśli chcesz zobaczyć, co się stanie po wstawieniu odstępu, Wstaw go po `$` znak, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="661b5-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="661b5-124">C# Kompilator wyświetla komunikat o błędzie "Błąd CS1056: Nieoczekiwany znak '$' ".)</span><span class="sxs-lookup"><span data-stu-id="661b5-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="661b5-125">Co najmniej jeden *wyrażeń interpolowanych*.</span><span class="sxs-lookup"><span data-stu-id="661b5-125">One or more *interpolated expressions*.</span></span> <span data-ttu-id="661b5-126">Wyrażenie interpolowane jest wskazywane przez nawias klamrowy otwierający i zamykający (`{` i `}`).</span><span class="sxs-lookup"><span data-stu-id="661b5-126">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="661b5-127">Możesz umieścić dowolne C# wyrażenie zwracające wartość (w tym `null`) wewnątrz nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="661b5-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="661b5-128">Wypróbujmy kilka dodatkowych przykładowych interpolacji ciągu z innymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="661b5-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="661b5-129">Uwzględnianie innych typów danych</span><span class="sxs-lookup"><span data-stu-id="661b5-129">Include different data types</span></span>

<span data-ttu-id="661b5-130">W poprzedniej sekcji Interpolacja ciągów jest używany do wstawienia jednego ciągu wewnątrz innego.</span><span class="sxs-lookup"><span data-stu-id="661b5-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="661b5-131">Wynik wyrażenia interpolowanego może być dowolnego typu danych, mimo że.</span><span class="sxs-lookup"><span data-stu-id="661b5-131">The result of an interpolated expression can be of any data type, though.</span></span> <span data-ttu-id="661b5-132">Teraz zawierać wartości różnych typów danych w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="661b5-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="661b5-133">W poniższym przykładzie, najpierw należy zdefiniować [klasy](../../programming-guide/classes-and-structs/classes.md) — typ danych `Vegetable` zawierający `Name` [właściwość](../../properties.md) i `ToString` [metoda](../../methods.md), które [zastępuje](../../language-reference/keywords/override.md) zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="661b5-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="661b5-134">[ `public` Modyfikator dostępu](../../language-reference/keywords/public.md) sprawia, że tej metody jest dostępny dla dowolnego kodu klienta, można pobrać reprezentacji w postaci ciągu `Vegetable` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="661b5-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="661b5-135">W przykładzie `Vegetable.ToString` metoda zwraca wartość `Name` właściwości, który jest inicjowany w `Vegetable` [Konstruktor](../../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="661b5-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="661b5-136">Następnie tworzymy wystąpienie `Vegetable` klasę o nazwie `item` przy użyciu [ `new` — słowo kluczowe](../../language-reference/keywords/new-operator.md) i podanie nazwy dla konstruktora `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="661b5-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` keyword](../../language-reference/keywords/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="661b5-137">Na koniec dołączamy `item` zmiennej do ciągu interpolowanego, który zawiera także <xref:System.DateTime> wartość <xref:System.Decimal> wartości i `Unit` [wyliczenie](../../programming-guide/enumeration-types.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="661b5-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="661b5-138">Zastąp cały kod C# w edytorze następującym kodem, a następnie użyj `dotnet run` polecenie, aby go uruchomić:</span><span class="sxs-lookup"><span data-stu-id="661b5-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="661b5-139">Należy pamiętać, że wyrażenie interpolowane `item` w ciągu interpolowanym jest rozpoznawany jako tekst "eggplant" w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="661b5-139">Note that the interpolated expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="661b5-140">To dlatego, gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest tłumaczona na ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="661b5-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="661b5-141">Jeśli wyrażenie interpolowane daje w wyniku `null`, ciąg pusty ("", lub <xref:System.String.Empty?displayProperty=nameWithType>) jest używany.</span><span class="sxs-lookup"><span data-stu-id="661b5-141">If the interpolated expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="661b5-142">Jeśli wyrażenie interpolowane nie mają `null`, zazwyczaj `ToString` zostanie wywołana metoda typ wyniku.</span><span class="sxs-lookup"><span data-stu-id="661b5-142">If the interpolated expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="661b5-143">Można to sprawdzić, aktualizując wykonania `Vegetable.ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="661b5-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="661b5-144">Może nawet trzeba zaimplementować `ToString` metody, ponieważ każdy typ ma pewne implementacja tej metody.</span><span class="sxs-lookup"><span data-stu-id="661b5-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="661b5-145">Aby to przetestować, przekształcić w komentarz definicję `Vegetable.ToString` metody w przykładzie (w tym celu należy umieścić symbol komentarza `//`, przed nim).</span><span class="sxs-lookup"><span data-stu-id="661b5-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="661b5-146">W danych wyjściowych ciąg "eggplant" został zastąpiony w pełni kwalifikowana nazwa typu ("roślinnego" w tym przykładzie), który jest domyślnym zachowaniem z <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="661b5-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="661b5-147">Domyślne zachowanie `ToString` metodą wartość wyliczenia jest zwraca reprezentację ciągu wartości.</span><span class="sxs-lookup"><span data-stu-id="661b5-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="661b5-148">W danych wyjściowych z tego przykładu Data jest zbyt precyzyjna (cena eggplant nie zmienia się każda sekunda), a wartość ceny nie wskazuje jednostkę waluty.</span><span class="sxs-lookup"><span data-stu-id="661b5-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="661b5-149">W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format ciągów reprezentujących wyniki wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="661b5-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="661b5-150">Kontrolowanie formatowania wyrażeń interpolowanych</span><span class="sxs-lookup"><span data-stu-id="661b5-150">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="661b5-151">W poprzedniej sekcji dwa nie najlepiej sformatowane ciągi zostały wstawione do ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="661b5-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="661b5-152">Jedna była wartość daty i godziny, dla którego tylko data powinna mieć zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="661b5-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="661b5-153">Drugim była cena, która nie wskazywała waluty.</span><span class="sxs-lookup"><span data-stu-id="661b5-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="661b5-154">Zarówno w przypadku problemów są łatwe do adresu.</span><span class="sxs-lookup"><span data-stu-id="661b5-154">Both issues are easy to address.</span></span> <span data-ttu-id="661b5-155">Interpolacja ciągów pozwala określić *ciągi formatujące* które kontrolują formatowanie poszczególnych typów.</span><span class="sxs-lookup"><span data-stu-id="661b5-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="661b5-156">Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby dołączyć ciągi formatu daty i ceny wyrażeń, jak pokazano w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="661b5-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="661b5-157">Należy określić ciąg formatu, postępując zgodnie z wyrażenia interpolowanego z dwukropkiem (":") i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="661b5-157">You specify a format string by following the interpolated expression with a colon (":") and the format string.</span></span> <span data-ttu-id="661b5-158">"d" jest [ciąg formatu standardowego daty i godziny](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) reprezentujący formatu daty krótkiej.</span><span class="sxs-lookup"><span data-stu-id="661b5-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="661b5-159">"C2" to [standardowy Ciąg formatujący](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) reprezentujący liczbę jako wartość waluty z dwoma cyframi po separatorze dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="661b5-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="661b5-160">Liczba typów w bibliotekach .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatu.</span><span class="sxs-lookup"><span data-stu-id="661b5-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="661b5-161">Dotyczy to wszystkich typów liczbowych i typów daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="661b5-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="661b5-162">Aby uzyskać pełną listę typów, które obsługują ciągi formatu, zobacz [ciągi formatu i typy biblioteki klas .NET](../../../standard/base-types/formatting-types.md#stringRef) w [typy formatowania na platformie .NET](../../../standard/base-types/formatting-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="661b5-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="661b5-163">Spróbuj zmodyfikować ciągi formatu w edytorze tekstu i, za każdym razem, wprowadzić zmiany, ponownie uruchom program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="661b5-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="661b5-164">Zmień "d" w `{date:d}` na "t" (Aby wyświetlić krótki format daty), "y" (Aby wyświetlić rok i miesiąc) oraz "yyyy" (Aby wyświetlać rok jako liczbę czterocyfrową).</span><span class="sxs-lookup"><span data-stu-id="661b5-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="661b5-165">Zmień "C2" w `{price:C2}` "e" (notacja wykładnicza) oraz "F3" (wartość liczbową z trzema cyframi po separatorze dziesiętnym).</span><span class="sxs-lookup"><span data-stu-id="661b5-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="661b5-166">Poza kontrolowaniem formatowania możesz też kontrolować szerokość pola i wyrównanie sformatowanego ciągów, które znajdują się w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="661b5-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="661b5-167">W następnej sekcji dowiesz się, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="661b5-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="661b5-168">Kontrolowanie szerokości pola i wyrównania wyrażeń interpolowanych</span><span class="sxs-lookup"><span data-stu-id="661b5-168">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="661b5-169">Zazwyczaj gdy wynikiem wyrażenia interpolowane jest sformatowany ciąg, ciąg znajduje się w ciągu wynikowym bez spacji wiodących albo końcowych.</span><span class="sxs-lookup"><span data-stu-id="661b5-169">Ordinarily, when the result of an interpolated expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="661b5-170">Szczególnie podczas pracy z zestawem danych, można kontrolować szerokość pola i wyrównanie tekstu pozwala tworzyć bardziej czytelny dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="661b5-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="661b5-171">Aby to zobaczyć, Zastąp cały kod w edytorze tekstu z następującym kodem, a następnie wpisz `dotnet run` do wykonania programu:</span><span class="sxs-lookup"><span data-stu-id="661b5-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="661b5-172">Nazwy autorzy są wyrównane do lewej, a tytułów, które one napisane są wyrównane do prawej.</span><span class="sxs-lookup"><span data-stu-id="661b5-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="661b5-173">Wyrównanie określa się poprzez dodanie przecinka (",") po wyrażenie interpolowane i wyznaczające *minimalne* szerokości pola.</span><span class="sxs-lookup"><span data-stu-id="661b5-173">You specify the alignment by adding a comma (",") after an interpolated expression and designating the *minimum* field width.</span></span> <span data-ttu-id="661b5-174">Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównany do prawej.</span><span class="sxs-lookup"><span data-stu-id="661b5-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="661b5-175">Jeśli jest liczbą ujemną, pole jest wyrównany do lewej.</span><span class="sxs-lookup"><span data-stu-id="661b5-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="661b5-176">Spróbuj usunąć znaki ujemne z `{"Author",-25}` i `{title.Key,-25}` kodu i uruchomić przykładowy kod ponownie, tak jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="661b5-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="661b5-177">Ten czas, informacje o autorze jest wyrównany do prawej.</span><span class="sxs-lookup"><span data-stu-id="661b5-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="661b5-178">Możesz połączyć specyfikator wyrównania i ciąg formatu dla pojedynczego wyrażenia interpolowane.</span><span class="sxs-lookup"><span data-stu-id="661b5-178">You can combine an alignment specifier and a format string for a single interpolated expression.</span></span> <span data-ttu-id="661b5-179">Aby to zrobić, określ wyrównanie najpierw następuje dwukropek i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="661b5-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="661b5-180">Zastąp cały kod wewnątrz `Main` metoda następującym kodem, który wyświetla trzy sformatowane ciągi ze zdefiniowanych szerokościami pól.</span><span class="sxs-lookup"><span data-stu-id="661b5-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="661b5-181">Następnie uruchom program, wprowadzając `dotnet run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="661b5-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="661b5-182">Dane wyjściowe wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="661b5-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="661b5-183">Pomyślnie ukończono samouczek interpolacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="661b5-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="661b5-184">Aby uzyskać więcej informacji, zobacz [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) tematu i [Interpolacja w języku C# ciągów](../../tutorials/string-interpolation.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="661b5-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
