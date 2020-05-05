---
title: Interpolacja ciągów — samouczek języka C#
description: W tym samouczku pokazano, jak za pomocą funkcji interpolacji ciągów języka C# uwzględnić sformatowane wyniki wyrażeń w większym ciągu.
ms.date: 10/23/2018
ms.openlocfilehash: d1b78670361e8b333499d12b68c0364ad9e40a85
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796057"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="e0c43-103">Użyj interpolacji ciągów, aby utworzyć sformatowane ciągi</span><span class="sxs-lookup"><span data-stu-id="e0c43-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="e0c43-104">W tym samouczku przedstawiono sposób użycia [interpolacji ciągu](../../language-reference/tokens/interpolated.md) języka C# do wstawiania wartości do pojedynczego ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="e0c43-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="e0c43-105">Napiszesz kod w języku C# i zobaczysz wyniki kompilacji i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="e0c43-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="e0c43-106">Samouczek zawiera serie lekcji pokazujące sposób wstawiania wartości do ciągu i formatowania tych wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="e0c43-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="e0c43-107">Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="e0c43-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="e0c43-108">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="e0c43-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="e0c43-109">Możesz również ukończyć [interaktywną wersję](interpolated-strings.yml) tego samouczka w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="e0c43-109">You can also complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="e0c43-110">Tworzenie ciągu interpolowanego</span><span class="sxs-lookup"><span data-stu-id="e0c43-110">Create an interpolated string</span></span>

<span data-ttu-id="e0c43-111">Utwórz katalog o nazwie *interpolowane*.</span><span class="sxs-lookup"><span data-stu-id="e0c43-111">Create a directory named *interpolated*.</span></span> <span data-ttu-id="e0c43-112">Ustaw jako bieżący katalog i uruchom następujące polecenie z okna konsoli:</span><span class="sxs-lookup"><span data-stu-id="e0c43-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="e0c43-113">To polecenie powoduje utworzenie nowej aplikacji konsolowej .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e0c43-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="e0c43-114">Otwórz *program.cs* w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem, w którym zastąpisz `<name>` swoją nazwę:</span><span class="sxs-lookup"><span data-stu-id="e0c43-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="e0c43-115">Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e0c43-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="e0c43-116">Kiedy uruchomisz program, zostanie wyświetlony jeden ciąg z Twoim imieniem w powitaniu.</span><span class="sxs-lookup"><span data-stu-id="e0c43-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="e0c43-117">Ciąg zawarty w wywołaniu <xref:System.Console.WriteLine%2A> metody jest *wyrażeniem ciągu interpolowanego*.</span><span class="sxs-lookup"><span data-stu-id="e0c43-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="e0c43-118">Jest to rodzaj szablonu, który umożliwia skonstruowanie pojedynczego ciągu (zwanego *ciągiem wynikowym*) z ciągu obejmującego osadzony kod.</span><span class="sxs-lookup"><span data-stu-id="e0c43-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="e0c43-119">Ciągi interpolowane są szczególnie użyteczne do wstawiania wartości do ciągu lub łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="e0c43-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="e0c43-120">Ten prosty przykład zawiera dwa elementy, które musi mieć każdy ciąg interpolowany:</span><span class="sxs-lookup"><span data-stu-id="e0c43-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="e0c43-121">Literał ciągu rozpoczynający się od znaku `$` przed otwierającym znakiem cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="e0c43-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="e0c43-122">Pomiędzy symbolem `$` i znakiem zapytania nie może być żadnych odstępów.</span><span class="sxs-lookup"><span data-stu-id="e0c43-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="e0c43-123">(Jeśli chcesz zobaczyć, co się stanie, jeśli dołączysz jeden, Wstaw spację po `$` znaku, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e0c43-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="e0c43-124">Kompilator języka C# wyświetla komunikat o błędzie "Error CS1056: nieoczekiwany znak" $ "".)</span><span class="sxs-lookup"><span data-stu-id="e0c43-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="e0c43-125">Co najmniej jedno *wyrażenie interpolacji*.</span><span class="sxs-lookup"><span data-stu-id="e0c43-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="e0c43-126">Wyrażenie interpolacji jest wskazywane przez otwierające i zamykające nawiasy`{` klamrowe (i `}`).</span><span class="sxs-lookup"><span data-stu-id="e0c43-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="e0c43-127">Do nawiasów klamrowych możesz wstawić dowolne wyrażenie języka C# zwracające wartość (w tym `null`).</span><span class="sxs-lookup"><span data-stu-id="e0c43-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="e0c43-128">Wypróbujmy kilka przykładów interpolacji ciągów z innymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="e0c43-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="e0c43-129">Uwzględnianie innych typów danych</span><span class="sxs-lookup"><span data-stu-id="e0c43-129">Include different data types</span></span>

<span data-ttu-id="e0c43-130">W poprzedniej sekcji użyto interpolacji ciągu do wstawienia jednego ciągu wewnątrz innego.</span><span class="sxs-lookup"><span data-stu-id="e0c43-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="e0c43-131">Wynik wyrażenia interpolacji może być dowolnego typu danych, chociaż.</span><span class="sxs-lookup"><span data-stu-id="e0c43-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="e0c43-132">Dołączmy wartości różnych typów danych w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="e0c43-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="e0c43-133">W poniższym przykładzie najpierw zdefiniujemy typ `Vegetable` danych [klasy](../../programming-guide/classes-and-structs/classes.md) , który ma `Name` [Właściwość](../../properties.md) i `ToString` [metodę](../../methods.md), która [zastępuje](../../language-reference/keywords/override.md) zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e0c43-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e0c43-134">[ `public` Modyfikator dostępu](../../language-reference/keywords/public.md) sprawia, że ta metoda jest dostępna dla dowolnego kodu klienta, aby uzyskać ciąg reprezentujący `Vegetable` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="e0c43-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="e0c43-135">W przykładzie `Vegetable.ToString` Metoda zwraca wartość `Name` właściwości, która została zainicjowana w `Vegetable` [konstruktorze](../../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="e0c43-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="e0c43-136">`Vegetable` Następnie tworzymy wystąpienie klasy o `item` nazwie przy użyciu [ `new` operatora](../../language-reference/operators/new-operator.md) i dostarczając nazwę konstruktora: `Vegetable`</span><span class="sxs-lookup"><span data-stu-id="e0c43-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="e0c43-137">Na `item` koniec dołączymy zmienną do ciągu interpolowanego, który <xref:System.DateTime> zawiera również wartość, <xref:System.Decimal> wartość i `Unit` wartość [wyliczenia](../../language-reference/builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="e0c43-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../language-reference/builtin-types/enum.md) value.</span></span> <span data-ttu-id="e0c43-138">Zamień cały kod C# w edytorze na następujący kod, a następnie użyj `dotnet run` polecenia, aby go uruchomić:</span><span class="sxs-lookup"><span data-stu-id="e0c43-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="e0c43-139">Należy zauważyć, że wyrażenie `item` interpolacji w ciągu interpolowanym jest rozpoznawane jako tekst "oberżyn" w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="e0c43-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="e0c43-140">Dzieje się tak, ponieważ, gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest rozpoznawany jako ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e0c43-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="e0c43-141">Jeśli wyrażenie interpolacji ma wartość `null`, jest używany pusty ciąg ("" lub <xref:System.String.Empty?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="e0c43-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="e0c43-142">Jeśli wyrażenie interpolacji nie jest szacowane do `null`, zazwyczaj wywoływana `ToString` jest metoda typu wynik.</span><span class="sxs-lookup"><span data-stu-id="e0c43-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="e0c43-143">Można to przetestować, aktualizując implementację `Vegetable.ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="e0c43-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="e0c43-144">Być może nie trzeba nawet implementować metody `ToString` , ponieważ każdy typ ma pewną implementację tej metody.</span><span class="sxs-lookup"><span data-stu-id="e0c43-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="e0c43-145">Aby to przetestować, Dodaj komentarz do definicji `Vegetable.ToString` metody w przykładzie (w tym celu należy umieścić symbol `//`komentarza, przed nim).</span><span class="sxs-lookup"><span data-stu-id="e0c43-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="e0c43-146">W danych wyjściowych ciąg "oberżyny" jest zamieniany przez w pełni kwalifikowaną nazwę typu ("warzywa" w tym przykładzie), która jest domyślnym zachowaniem <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e0c43-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e0c43-147">Domyślnym zachowaniem `ToString` metody dla wartości wyliczenia jest zwrócenie ciągu reprezentującego wartość.</span><span class="sxs-lookup"><span data-stu-id="e0c43-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="e0c43-148">W danych wyjściowych tego przykładu Data jest zbyt dokładna (cena oberżyny nie zmienia się co sekundę), a wartość ceny nie wskazuje jednostki waluty.</span><span class="sxs-lookup"><span data-stu-id="e0c43-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="e0c43-149">W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format wyników wyrażenia w postaci ciągów.</span><span class="sxs-lookup"><span data-stu-id="e0c43-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="e0c43-150">Sterowanie formatowaniem wyrażeń interpolacji</span><span class="sxs-lookup"><span data-stu-id="e0c43-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="e0c43-151">W poprzedniej sekcji dwa niewłaściwie sformatowane ciągi zostały wstawione do ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="e0c43-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="e0c43-152">Jednym z nich była wartość daty i godziny, chociaż tylko data powinna mieć zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="e0c43-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="e0c43-153">Druga cena była ceną, która nie wskazywała swojej jednostki waluty.</span><span class="sxs-lookup"><span data-stu-id="e0c43-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="e0c43-154">Oba problemy można z łatwością rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="e0c43-154">Both issues are easy to address.</span></span> <span data-ttu-id="e0c43-155">Interpolacja ciągów pozwala określić *ciągi formatowania* , które kontrolują formatowanie poszczególnych typów.</span><span class="sxs-lookup"><span data-stu-id="e0c43-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="e0c43-156">Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby uwzględnić ciągi formatu dla wyrażeń daty i ceny, jak pokazano w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="e0c43-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="e0c43-157">Ciąg formatu można określić, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągiem formatu.</span><span class="sxs-lookup"><span data-stu-id="e0c43-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="e0c43-158">„d” jest [standardowym ciągiem formatu daty i godziny](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), który reprezentuje krótki format daty.</span><span class="sxs-lookup"><span data-stu-id="e0c43-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="e0c43-159">„C2” to [standardowy ciąg formatu numerycznego](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), który reprezentuje liczbę jako wartość waluty z dwoma cyframi po separatorze dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="e0c43-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="e0c43-160">Wiele typów w bibliotekach .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatujących.</span><span class="sxs-lookup"><span data-stu-id="e0c43-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="e0c43-161">Uwzględnia to wszystkie typy numeryczne oraz typy daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="e0c43-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="e0c43-162">Aby uzyskać kompletną listę typów, które obsługują ciągi formatu, zobacz [Ciągi formatu i typy biblioteki klas .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) w artykule [Typy formatowania na platformie .NET](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="e0c43-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="e0c43-163">Spróbuj zmodyfikować ciągi formatu w edytorze tekstów i, przy każdym wprowadzeniu zmiany, uruchom ponownie program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="e0c43-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="e0c43-164">Zmień „d” w ciągu `{date:d}` na „t” (aby wyświetlić krótki format daty), „y” (aby wyświetlić rok i miesiąc) oraz „yyyy” (aby wyświetlać rok jako liczbę czterocyfrową).</span><span class="sxs-lookup"><span data-stu-id="e0c43-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="e0c43-165">Zmień „C2” w ciągu `{price:C2}` na „e” (notacja wykładnicza) oraz „F3” (wartość numeryczna z trzema cyframi po separatorze dziesiętnym).</span><span class="sxs-lookup"><span data-stu-id="e0c43-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="e0c43-166">Oprócz kontrolowania formatowania można również kontrolować szerokość pola i wyrównanie sformatowanych ciągów, które są uwzględnione w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="e0c43-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="e0c43-167">W następnej sekcji dowiesz się, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="e0c43-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="e0c43-168">Kontrolowanie szerokości pola i wyrównania wyrażeń interpolacji</span><span class="sxs-lookup"><span data-stu-id="e0c43-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="e0c43-169">Zwykle, gdy wynik wyrażenia interpolacji jest sformatowany do ciągu, ten ciąg jest uwzględniany w ciągu wynikowym bez spacji wiodących i końcowych.</span><span class="sxs-lookup"><span data-stu-id="e0c43-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="e0c43-170">Szczególnie podczas pracy z zestawem danych, możliwość kontrolowania szerokości pola i wyrównania tekstu pomaga utworzyć bardziej czytelny wynik.</span><span class="sxs-lookup"><span data-stu-id="e0c43-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="e0c43-171">Aby to zobaczyć, Zastąp cały kod w edytorze tekstu następującym kodem, a następnie wpisz `dotnet run` , aby wykonać program:</span><span class="sxs-lookup"><span data-stu-id="e0c43-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="e0c43-172">Nazwy autorów są wyrównane do lewej, a napisane tytuły są wyrównane do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="e0c43-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="e0c43-173">Wyrównanie należy określić przez dodanie przecinka (",") po wyrażeniu interpolacji i wyznaczenie *minimalnej* szerokości pola.</span><span class="sxs-lookup"><span data-stu-id="e0c43-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="e0c43-174">Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównane do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="e0c43-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="e0c43-175">Jeśli jest to liczba ujemna, pole jest wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="e0c43-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="e0c43-176">Spróbuj usunąć znaki ujemne z kodu `{"Author",-25}` i `{title.Key,-25}` i ponownie uruchomić przykład, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e0c43-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="e0c43-177">Tym razem informacje o autorze są wyrównane do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="e0c43-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="e0c43-178">Można połączyć specyfikator wyrównania i ciąg formatu dla pojedynczego wyrażenia interpolacji.</span><span class="sxs-lookup"><span data-stu-id="e0c43-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="e0c43-179">W tym celu należy określić wyrównania jako pierwsze, po którym następuje dwukropek i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="e0c43-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="e0c43-180">Zamień cały kod wewnątrz `Main` metody na następujący kod, który wyświetla trzy sformatowane ciągi ze zdefiniowanymi szerokościami pól.</span><span class="sxs-lookup"><span data-stu-id="e0c43-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="e0c43-181">Następnie uruchom program, wprowadzając `dotnet run` polecenie.</span><span class="sxs-lookup"><span data-stu-id="e0c43-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="e0c43-182">Dane wyjściowe wyglądają podobnie do następujących:</span><span class="sxs-lookup"><span data-stu-id="e0c43-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="e0c43-183">Samouczek interpolacji ciągów został ukończony.</span><span class="sxs-lookup"><span data-stu-id="e0c43-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="e0c43-184">Aby uzyskać więcej informacji, zobacz temat [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) i [Interpolacja ciągów w samouczku języka C#](../string-interpolation.md) .</span><span class="sxs-lookup"><span data-stu-id="e0c43-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../string-interpolation.md) tutorial.</span></span>
