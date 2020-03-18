---
title: Interpolacja ciągów — samouczek języka C#
description: W tym samouczku pokazano, jak używać funkcji interpolacji ciągów C# do uwzględnienia sformatowanych wyników wyrażeń w większym ciągu.
ms.date: 10/23/2018
ms.openlocfilehash: 593f3a77370da73dfd5f090be98112327b86b1f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346777"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="3aa51-103">Używanie interpolacji ciągów do konstruowania sformatowanych ciągów</span><span class="sxs-lookup"><span data-stu-id="3aa51-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="3aa51-104">W tym samouczku nauczy cię, jak używać [interpolacji ciągów](../../language-reference/tokens/interpolated.md) C# do wstawiania wartości do jednego ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="3aa51-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="3aa51-105">Piszesz kod C# i zobaczyć wyniki kompilacji i uruchamiania go.</span><span class="sxs-lookup"><span data-stu-id="3aa51-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="3aa51-106">Samouczek zawiera serię lekcji, które pokazują, jak wstawić wartości do ciągu i sformatować te wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="3aa51-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="3aa51-107">Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia.</span><span class="sxs-lookup"><span data-stu-id="3aa51-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="3aa51-108">Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="3aa51-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="3aa51-109">Możesz również ukończyć [interaktywną wersję](interpolated-strings.yml) tego samouczka w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="3aa51-109">You also can complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="3aa51-110">Tworzenie ciągu interpolowanego</span><span class="sxs-lookup"><span data-stu-id="3aa51-110">Create an interpolated string</span></span>

<span data-ttu-id="3aa51-111">Utwórz katalog o nazwie *interpolowany*.</span><span class="sxs-lookup"><span data-stu-id="3aa51-111">Create a directory named *interpolated*.</span></span> <span data-ttu-id="3aa51-112">Uczyń go bieżącym katalogiem i uruchom następujące polecenie z okna konsoli:</span><span class="sxs-lookup"><span data-stu-id="3aa51-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="3aa51-113">To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3aa51-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="3aa51-114">Otwórz *Program.cs* w ulubionym edytorze `Console.WriteLine("Hello World!");` i zastąp wiersz `<name>` następującym kodem, w którym możesz zastąpić swoje imię i nazwisko:</span><span class="sxs-lookup"><span data-stu-id="3aa51-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="3aa51-115">Wypróbuj `dotnet run` ten kod, wpisując w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="3aa51-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="3aa51-116">Kiedy uruchomisz program, zostanie wyświetlony jeden ciąg z Twoim imieniem w powitaniu.</span><span class="sxs-lookup"><span data-stu-id="3aa51-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="3aa51-117">Ciąg zawarty <xref:System.Console.WriteLine%2A> w wywołaniu metody jest *interpolowanym wyrażeniem ciągu*.</span><span class="sxs-lookup"><span data-stu-id="3aa51-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="3aa51-118">Jest to rodzaj szablonu, który umożliwia skonstruowanie pojedynczego ciągu (zwanego *ciągiem wynikowym*) z ciągu obejmującego osadzony kod.</span><span class="sxs-lookup"><span data-stu-id="3aa51-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="3aa51-119">Ciągi interpolowane są szczególnie użyteczne do wstawiania wartości do ciągu lub łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="3aa51-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="3aa51-120">Ten prosty przykład zawiera dwa elementy, które musi mieć każdy ciąg interpolowany:</span><span class="sxs-lookup"><span data-stu-id="3aa51-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="3aa51-121">Literał ciągu rozpoczynający się od znaku `$` przed otwierającym znakiem cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="3aa51-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="3aa51-122">Pomiędzy symbolem `$` i znakiem zapytania nie może być żadnych odstępów.</span><span class="sxs-lookup"><span data-stu-id="3aa51-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="3aa51-123">(Jeśli chcesz zobaczyć, co się stanie, jeśli go dodasz, wstaw spacja po `$` znaku, `dotnet run` zapisz plik i uruchom program ponownie, wpisując go w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="3aa51-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="3aa51-124">Kompilator C# wyświetla komunikat o błędzie "błąd CS1056: Nieoczekiwany znak '$'".)</span><span class="sxs-lookup"><span data-stu-id="3aa51-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="3aa51-125">Jedno lub więcej *wyrażeń interpolacji*.</span><span class="sxs-lookup"><span data-stu-id="3aa51-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="3aa51-126">Wyrażenie interpolacji jest oznaczone nawiasem klamrowym otwierania i zamykania (`{` i `}`).</span><span class="sxs-lookup"><span data-stu-id="3aa51-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="3aa51-127">Do nawiasów klamrowych możesz wstawić dowolne wyrażenie języka C# zwracające wartość (w tym `null`).</span><span class="sxs-lookup"><span data-stu-id="3aa51-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="3aa51-128">Spróbujmy kilka przykładów interpolacji ciągów z niektórych innych typów danych.</span><span class="sxs-lookup"><span data-stu-id="3aa51-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="3aa51-129">Uwzględnianie innych typów danych</span><span class="sxs-lookup"><span data-stu-id="3aa51-129">Include different data types</span></span>

<span data-ttu-id="3aa51-130">W poprzedniej sekcji użyto interpolacji ciągów, aby wstawić jeden ciąg wewnątrz innego.</span><span class="sxs-lookup"><span data-stu-id="3aa51-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="3aa51-131">Wynik wyrażenia interpolacji może być dowolnego typu danych, choć.</span><span class="sxs-lookup"><span data-stu-id="3aa51-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="3aa51-132">Uwzględnijmy wartości różnych typów danych w interpolowanym ciągu.</span><span class="sxs-lookup"><span data-stu-id="3aa51-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="3aa51-133">W poniższym przykładzie najpierw definiujemy `Vegetable` typ danych `Name` [klasy,](../../programming-guide/classes-and-structs/classes.md) który ma [właściwość](../../properties.md) i `ToString` <xref:System.Object.ToString?displayProperty=nameWithType> [metodę](../../methods.md), która [zastępuje](../../language-reference/keywords/override.md) zachowanie metody.</span><span class="sxs-lookup"><span data-stu-id="3aa51-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3aa51-134">[ `public` Modyfikator dostępu](../../language-reference/keywords/public.md) udostępnia tę metodę do dowolnego kodu `Vegetable` klienta, aby uzyskać reprezentację ciągu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3aa51-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="3aa51-135">W przykładzie `Vegetable.ToString` metoda zwraca wartość `Name` właściwości, która jest `Vegetable` inicjowana w [konstruktorze:](../../programming-guide/classes-and-structs/constructors.md)</span><span class="sxs-lookup"><span data-stu-id="3aa51-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="3aa51-136">Następnie tworzymy wystąpienie `Vegetable` klasy `item` o nazwie przy użyciu [ `new` operatora](../../language-reference/operators/new-operator.md) i podając nazwę dla konstruktora: `Vegetable`</span><span class="sxs-lookup"><span data-stu-id="3aa51-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="3aa51-137">Na koniec możemy `item` dołączyć zmienną do interpolowany <xref:System.DateTime> ciąg, <xref:System.Decimal> który zawiera `Unit` również wartość, wartość i wartość [wyliczenia.](../../language-reference/builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="3aa51-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../language-reference/builtin-types/enum.md) value.</span></span> <span data-ttu-id="3aa51-138">Zastąp cały kod Języka C# w edytorze `dotnet run` następującym kodem, a następnie użyj polecenia, aby go uruchomić:</span><span class="sxs-lookup"><span data-stu-id="3aa51-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="3aa51-139">Należy zauważyć, że `item` wyrażenie interpolacji w interpolowanym ciągu jest rozpoznawane z tekstem "bakłażan" w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="3aa51-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="3aa51-140">Dzieje się tak, ponieważ gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest rozpoznawany do ciągu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3aa51-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="3aa51-141">Jeśli wyrażenie interpolacji jest `null`oceniane , jest używany <xref:System.String.Empty?displayProperty=nameWithType>pusty ciąg ("", lub ) .</span><span class="sxs-lookup"><span data-stu-id="3aa51-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="3aa51-142">Jeśli wyrażenie interpolacji nie ocenia `null`, zazwyczaj `ToString` nazywa się metodę typu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="3aa51-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="3aa51-143">Można to przetestować, aktualizując `Vegetable.ToString` implementację metody.</span><span class="sxs-lookup"><span data-stu-id="3aa51-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="3aa51-144">Może nawet nie trzeba `ToString` zaimplementować metodę, ponieważ każdy typ ma implementację tej metody.</span><span class="sxs-lookup"><span data-stu-id="3aa51-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="3aa51-145">Aby to przetestować, skomentuj `Vegetable.ToString` definicję metody w przykładzie (aby to `//`zrobić, umieść symbol komentarza, przed nim).</span><span class="sxs-lookup"><span data-stu-id="3aa51-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="3aa51-146">W danych wyjściowych ciąg "bakłażan" jest zastępowany w pełni kwalifikowaną nazwą typu ("Warzywo" w tym przykładzie), która jest domyślnym zachowaniem <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3aa51-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3aa51-147">Domyślnym zachowaniem `ToString` metody dla wartości wyliczenia jest zwrócenie reprezentacji ciągu wartości.</span><span class="sxs-lookup"><span data-stu-id="3aa51-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="3aa51-148">W danych wyjściowych z tego przykładu data jest zbyt precyzyjna (cena bakłażana nie zmienia się co sekundę), a wartość ceny nie wskazuje jednostki waluty.</span><span class="sxs-lookup"><span data-stu-id="3aa51-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="3aa51-149">W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format reprezentacji ciągów wyników wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3aa51-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="3aa51-150">Sterowanie formatowaniem wyrażeń interpolacji</span><span class="sxs-lookup"><span data-stu-id="3aa51-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="3aa51-151">W poprzedniej sekcji dwa źle sformatowane ciągi zostały wstawione do ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="3aa51-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="3aa51-152">Jednym z nich była wartość daty i godziny, chociaż tylko data powinna mieć zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="3aa51-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="3aa51-153">Druga to cena, która nie wskazywała na jednostkę waluty.</span><span class="sxs-lookup"><span data-stu-id="3aa51-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="3aa51-154">Oba problemy można z łatwością rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="3aa51-154">Both issues are easy to address.</span></span> <span data-ttu-id="3aa51-155">Interpolacja ciągów umożliwia określenie *formatów,* które kontrolują formatowanie określonych typów.</span><span class="sxs-lookup"><span data-stu-id="3aa51-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="3aa51-156">Zmodyfikuj wywołanie z poprzedniego przykładu, aby `Console.WriteLine` uwzględnić ciągi formatu dla wyrażeń daty i ceny, jak pokazano w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="3aa51-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="3aa51-157">Ciąg formatu można określić, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągiem formatu.</span><span class="sxs-lookup"><span data-stu-id="3aa51-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="3aa51-158">„d” jest [standardowym ciągiem formatu daty i godziny](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), który reprezentuje krótki format daty.</span><span class="sxs-lookup"><span data-stu-id="3aa51-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="3aa51-159">„C2” to [standardowy ciąg formatu numerycznego](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), który reprezentuje liczbę jako wartość waluty z dwoma cyframi po separatorze dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="3aa51-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="3aa51-160">Wiele typów w bibliotekach .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatu.</span><span class="sxs-lookup"><span data-stu-id="3aa51-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="3aa51-161">Uwzględnia to wszystkie typy numeryczne oraz typy daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="3aa51-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="3aa51-162">Aby uzyskać kompletną listę typów, które obsługują ciągi formatu, zobacz [Ciągi formatu i typy biblioteki klas .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) w artykule [Typy formatowania na platformie .NET](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="3aa51-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="3aa51-163">Spróbuj zmodyfikować ciągi formatu w edytorze tekstu i za każdym razem, gdy wprowadzasz zmianę, uruchom ponownie program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="3aa51-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="3aa51-164">Zmień „d” w ciągu `{date:d}` na „t” (aby wyświetlić krótki format daty), „y” (aby wyświetlić rok i miesiąc) oraz „yyyy” (aby wyświetlać rok jako liczbę czterocyfrową).</span><span class="sxs-lookup"><span data-stu-id="3aa51-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="3aa51-165">Zmień „C2” w ciągu `{price:C2}` na „e” (notacja wykładnicza) oraz „F3” (wartość numeryczna z trzema cyframi po separatorze dziesiętnym).</span><span class="sxs-lookup"><span data-stu-id="3aa51-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="3aa51-166">Oprócz sterowania formatowaniem można również sterować szerokością pola i wyrównaniem sformatowanych ciągów, które są zawarte w ciągu wyników.</span><span class="sxs-lookup"><span data-stu-id="3aa51-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="3aa51-167">W następnej sekcji dowiesz się, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="3aa51-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="3aa51-168">Sterowanie szerokością pola i wyrównaniem wyrażeń interpolacji</span><span class="sxs-lookup"><span data-stu-id="3aa51-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="3aa51-169">Zwykle, gdy wynik wyrażenia interpolacji jest sformatowany na ciąg, ten ciąg jest dołączony do ciągu wynikowego bez spacji wiodących lub końcowych.</span><span class="sxs-lookup"><span data-stu-id="3aa51-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="3aa51-170">Szczególnie podczas pracy z zestawem danych, możliwość kontrolowania szerokości pola i wyrównania tekstu pomaga uzyskać bardziej czytelne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3aa51-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="3aa51-171">Aby to zobaczyć, zamień cały kod w edytorze `dotnet run` tekstu następującym kodem, a następnie wpisz, aby wykonać program:</span><span class="sxs-lookup"><span data-stu-id="3aa51-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="3aa51-172">Nazwiska autorów są wyrównane do lewej, a tytuły, które napisali, są wyrównane do prawej.</span><span class="sxs-lookup"><span data-stu-id="3aa51-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="3aa51-173">Wyrównanie należy określić, dodając przecinek (",") po wyrażeniu interpolacji i wyznaczając *minimalną* szerokość pola.</span><span class="sxs-lookup"><span data-stu-id="3aa51-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="3aa51-174">Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównane do prawej.</span><span class="sxs-lookup"><span data-stu-id="3aa51-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="3aa51-175">Jeśli jest to liczba ujemna, pole jest wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="3aa51-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="3aa51-176">Spróbuj usunąć znaki ujemne z `{"Author",-25}` kodu i `{title.Key,-25}` ponownie uruchomić przykład, jak to robi następujący kod:</span><span class="sxs-lookup"><span data-stu-id="3aa51-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="3aa51-177">Tym razem informacje autora są wyrównane do prawej.</span><span class="sxs-lookup"><span data-stu-id="3aa51-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="3aa51-178">Można połączyć specyfikator wyrównania i ciąg formatu dla pojedynczego wyrażenia interpolacji.</span><span class="sxs-lookup"><span data-stu-id="3aa51-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="3aa51-179">Aby to zrobić, najpierw określ wyrównanie, a następnie dwukropek i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="3aa51-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="3aa51-180">Zamień cały kod `Main` wewnątrz metody na następujący kod, który wyświetla trzy sformatowane ciągi o zdefiniowanych szerokościach pól.</span><span class="sxs-lookup"><span data-stu-id="3aa51-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="3aa51-181">Następnie uruchom program, wprowadzając `dotnet run` polecenie.</span><span class="sxs-lookup"><span data-stu-id="3aa51-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="3aa51-182">Dane wyjściowe wyglądają mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="3aa51-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="3aa51-183">Ukończono samouczek interpolacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="3aa51-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="3aa51-184">Aby uzyskać więcej informacji, zobacz [temat Interpolacji ciąg](../../language-reference/tokens/interpolated.md) ów i [Interpolacji ciąg w języku C#tutorial.](../../tutorials/string-interpolation.md)</span><span class="sxs-lookup"><span data-stu-id="3aa51-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
