---
title: Interpolacja ciągów — C# samouczek
description: W tym samouczku pokazano, jak za C# pomocą funkcji interpolacji ciągów dołączać sformatowane wyniki wyrażeń w większym ciągu.
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: b2bbab5705d78525ccae6a90b4f4f2a91064a06b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117850"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="96227-103">Użyj interpolacji ciągów, aby utworzyć sformatowane ciągi</span><span class="sxs-lookup"><span data-stu-id="96227-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="96227-104">W tym samouczku przedstawiono sposób użycia C# [interpolacji ciągu](../../language-reference/tokens/interpolated.md) do wstawiania wartości w postaci pojedynczego ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="96227-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="96227-105">Napiszesz C# kod i zobaczysz wyniki kompilacji i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="96227-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="96227-106">Samouczek zawiera serie lekcji pokazujące sposób wstawiania wartości do ciągu i formatowania tych wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="96227-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="96227-107">Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="96227-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="96227-108">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego na komputerach Mac, komputerze lub Linux.</span><span class="sxs-lookup"><span data-stu-id="96227-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="96227-109">Możesz również ukończyć [interaktywną wersję](interpolated-strings.yml) tego samouczka w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="96227-109">You also can complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="96227-110">Utwórz ciąg interpolowany</span><span class="sxs-lookup"><span data-stu-id="96227-110">Create an interpolated string</span></span>

<span data-ttu-id="96227-111">Utwórz katalog o nazwie **interpolowane**.</span><span class="sxs-lookup"><span data-stu-id="96227-111">Create a directory named **interpolated**.</span></span> <span data-ttu-id="96227-112">Ustaw jako bieżący katalog i uruchom następujące polecenie z okna konsoli:</span><span class="sxs-lookup"><span data-stu-id="96227-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="96227-113">To polecenie powoduje utworzenie nowej aplikacji konsolowej .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="96227-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="96227-114">Otwórz **program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem, w którym zastąpisz `<name>` swoją nazwę:</span><span class="sxs-lookup"><span data-stu-id="96227-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="96227-115">Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="96227-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="96227-116">Po uruchomieniu programu w powitaniu zostanie wyświetlony pojedynczy ciąg zawierający nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="96227-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="96227-117">Ciąg zawarty w <xref:System.Console.WriteLine%2A> wywołaniu metody jest *wyrażeniem ciągu interpolowanego*.</span><span class="sxs-lookup"><span data-stu-id="96227-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="96227-118">Jest to rodzaj szablonu, który umożliwia konstruowanie pojedynczego ciągu (zwanego *ciągiem wynikowym*) z ciągu, który zawiera kod osadzony.</span><span class="sxs-lookup"><span data-stu-id="96227-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="96227-119">Ciąg interpolowany jest szczególnie przydatny do wstawiania wartości do ciągu lub łączenia (łączenie ze sobą) ciągów.</span><span class="sxs-lookup"><span data-stu-id="96227-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="96227-120">Ten prosty przykład zawiera dwa elementy, które każdy ciąg interpolowany musi mieć:</span><span class="sxs-lookup"><span data-stu-id="96227-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="96227-121">Literał ciągu zaczynający się od `$` znaku przed znakiem cudzysłowu otwierającego.</span><span class="sxs-lookup"><span data-stu-id="96227-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="96227-122">Między `$` symbolem i znakiem cudzysłowu nie mogą znajdować się spacje.</span><span class="sxs-lookup"><span data-stu-id="96227-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="96227-123">(Jeśli chcesz zobaczyć, co się stanie, jeśli dołączysz jeden, Wstaw spację po `$` znaku, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="96227-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="96227-124">C# Kompilator wyświetla komunikat o błędzie "błąd CS1056: Nieoczekiwany znak "$" ".)</span><span class="sxs-lookup"><span data-stu-id="96227-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="96227-125">Co najmniej jedno *wyrażenie interpolacji*.</span><span class="sxs-lookup"><span data-stu-id="96227-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="96227-126">Wyrażenie interpolacji jest wskazywane przez otwierające i zamykające nawiasy`{` klamrowe (i `}`).</span><span class="sxs-lookup"><span data-stu-id="96227-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="96227-127">Można umieścić dowolne C# Wyrażenie zwracające wartość (w tym `null`) w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="96227-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="96227-128">Wypróbujmy kilka przykładów interpolacji ciągów z innymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="96227-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="96227-129">Uwzględnij różne typy danych</span><span class="sxs-lookup"><span data-stu-id="96227-129">Include different data types</span></span>

<span data-ttu-id="96227-130">W poprzedniej sekcji użyto interpolacji ciągu do wstawienia jednego ciągu wewnątrz innego.</span><span class="sxs-lookup"><span data-stu-id="96227-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="96227-131">Wynik wyrażenia interpolacji może być dowolnego typu danych, chociaż.</span><span class="sxs-lookup"><span data-stu-id="96227-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="96227-132">Dołączmy wartości różnych typów danych w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="96227-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="96227-133">W poniższym przykładzie najpierw zdefiniujemy `Vegetable` typ danych [klasy](../../programming-guide/classes-and-structs/classes.md) , który ma `Name` [Właściwość](../../properties.md) i `ToString` [metodę](../../methods.md), która [zastępuje](../../language-reference/keywords/override.md) zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="96227-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="96227-134">[ `public` Modyfikator dostępu](../../language-reference/keywords/public.md) sprawia, że ta metoda jest dostępna dla dowolnego kodu klienta, aby uzyskać `Vegetable` ciąg reprezentujący wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="96227-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="96227-135">W przykładzie `Vegetable.ToString` Metoda zwraca wartość `Name` właściwości `Vegetable` , która została zainicjowana w [konstruktorze](../../programming-guide/classes-and-structs/constructors.md):</span><span class="sxs-lookup"><span data-stu-id="96227-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="96227-136">Następnie `Vegetable` tworzymy wystąpienie klasy o `item` nazwie przy użyciu [ `new` operatora](../../language-reference/operators/new-operator.md) i dostarczając nazwę konstruktora: `Vegetable`</span><span class="sxs-lookup"><span data-stu-id="96227-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="96227-137">Na `item` koniec dołączymy zmienną do ciągu interpolowanego, który <xref:System.DateTime> zawiera również wartość, <xref:System.Decimal> wartość i `Unit` wartość [wyliczenia](../../programming-guide/enumeration-types.md) .</span><span class="sxs-lookup"><span data-stu-id="96227-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="96227-138">Zastąp cały C# kod w edytorze następującym kodem, a następnie użyj `dotnet run` polecenia, aby go uruchomić:</span><span class="sxs-lookup"><span data-stu-id="96227-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="96227-139">Należy zauważyć, że wyrażenie `item` interpolacji w ciągu interpolowanym jest rozpoznawane jako tekst "oberżyn" w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="96227-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="96227-140">Dzieje się tak, ponieważ, gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest rozpoznawany jako ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="96227-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="96227-141">Jeśli wyrażenie interpolacji ma wartość `null`, jest używany pusty ciąg ("" lub <xref:System.String.Empty?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="96227-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="96227-142">Jeśli wyrażenie interpolacji nie jest szacowane do `null`, `ToString` zazwyczaj wywoływana jest metoda typu wynik.</span><span class="sxs-lookup"><span data-stu-id="96227-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="96227-143">Można to przetestować, aktualizując implementację `Vegetable.ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="96227-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="96227-144">Być może nie trzeba nawet implementować metody `ToString` , ponieważ każdy typ ma pewną implementację tej metody.</span><span class="sxs-lookup"><span data-stu-id="96227-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="96227-145">Aby to przetestować, Dodaj komentarz do definicji `Vegetable.ToString` metody w przykładzie (w tym celu należy umieścić `//`symbol komentarza, przed nim).</span><span class="sxs-lookup"><span data-stu-id="96227-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="96227-146">W danych wyjściowych ciąg "oberżyny" jest zamieniany przez w pełni kwalifikowaną nazwę typu ("warzywa" w tym przykładzie), która jest domyślnym zachowaniem <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="96227-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="96227-147">Domyślnym zachowaniem `ToString` metody dla wartości wyliczenia jest zwrócenie ciągu reprezentującego wartość.</span><span class="sxs-lookup"><span data-stu-id="96227-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="96227-148">W danych wyjściowych tego przykładu Data jest zbyt dokładna (cena oberżyny nie zmienia się co sekundę), a wartość ceny nie wskazuje jednostki waluty.</span><span class="sxs-lookup"><span data-stu-id="96227-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="96227-149">W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format wyników wyrażenia w postaci ciągów.</span><span class="sxs-lookup"><span data-stu-id="96227-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="96227-150">Sterowanie formatowaniem wyrażeń interpolacji</span><span class="sxs-lookup"><span data-stu-id="96227-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="96227-151">W poprzedniej sekcji dwa niewłaściwie sformatowane ciągi zostały wstawione do ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="96227-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="96227-152">Jedna była wartością daty i godziny, dla której jest właściwa tylko Data.</span><span class="sxs-lookup"><span data-stu-id="96227-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="96227-153">Druga cena była ceną, która nie wskazywała swojej jednostki waluty.</span><span class="sxs-lookup"><span data-stu-id="96227-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="96227-154">Oba problemy są łatwe w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="96227-154">Both issues are easy to address.</span></span> <span data-ttu-id="96227-155">Interpolacja ciągów pozwala określić *ciągi formatowania* , które kontrolują formatowanie poszczególnych typów.</span><span class="sxs-lookup"><span data-stu-id="96227-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="96227-156">Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby uwzględnić ciągi formatu dla wyrażeń daty i ceny, jak pokazano w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="96227-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="96227-157">Ciąg formatu można określić, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągiem formatu.</span><span class="sxs-lookup"><span data-stu-id="96227-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="96227-158">"d" to [standardowy ciąg formatu daty i godziny](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) , który reprezentuje format daty krótkiej.</span><span class="sxs-lookup"><span data-stu-id="96227-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="96227-159">"C2" to [standardowy ciąg formatu liczbowego](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) , który reprezentuje liczbę jako wartość walutową z dwiema cyframi po przecinku dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="96227-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="96227-160">Wiele typów w bibliotekach .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatujących.</span><span class="sxs-lookup"><span data-stu-id="96227-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="96227-161">Obejmują one wszystkie typy liczbowe i typy daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="96227-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="96227-162">Aby zapoznać się z pełną listą typów, które obsługują ciągi formatu, zobacz [ciągi formatowania i typy bibliotek klas .NET](../../../standard/base-types/formatting-types.md#stringRef) w [typach formatowania w artykule .NET](../../../standard/base-types/formatting-types.md) .</span><span class="sxs-lookup"><span data-stu-id="96227-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="96227-163">Spróbuj zmodyfikować ciągi formatu w edytorze tekstów i, przy każdym wprowadzeniu zmiany, uruchom ponownie program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="96227-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="96227-164">Zmień literę "d" `{date:d}` w "t" (aby wyświetlić format godziny krótkiej), "y" (w celu wyświetlenia roku i miesiąca) i "RRRR" (aby wyświetlić rok jako liczbę czterocyfrową).</span><span class="sxs-lookup"><span data-stu-id="96227-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="96227-165">Zmień wartość "C2" w `{price:C2}` na "e" (dla notacji wykładniczej) i "F3" (w przypadku wartości liczbowej z trzema cyframi po przecinku dziesiętnym).</span><span class="sxs-lookup"><span data-stu-id="96227-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="96227-166">Oprócz kontrolowania formatowania można również kontrolować szerokość pola i wyrównanie sformatowanych ciągów, które są uwzględnione w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="96227-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="96227-167">W następnej sekcji dowiesz się, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="96227-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="96227-168">Kontrolowanie szerokości pola i wyrównania wyrażeń interpolacji</span><span class="sxs-lookup"><span data-stu-id="96227-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="96227-169">Zwykle, gdy wynik wyrażenia interpolacji jest sformatowany do ciągu, ten ciąg jest uwzględniany w ciągu wynikowym bez spacji wiodących i końcowych.</span><span class="sxs-lookup"><span data-stu-id="96227-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="96227-170">Szczególnie podczas pracy z zestawem danych, możliwość kontrolowania szerokości pola i wyrównania tekstu pomaga utworzyć bardziej czytelny wynik.</span><span class="sxs-lookup"><span data-stu-id="96227-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="96227-171">Aby to zobaczyć, Zastąp cały kod w edytorze tekstu następującym kodem, a następnie wpisz `dotnet run` , aby wykonać program:</span><span class="sxs-lookup"><span data-stu-id="96227-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="96227-172">Nazwy autorów są wyrównane do lewej, a napisane tytuły są wyrównane do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="96227-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="96227-173">Wyrównanie należy określić przez dodanie przecinka (",") po wyrażeniu interpolacji i wyznaczenie *minimalnej* szerokości pola.</span><span class="sxs-lookup"><span data-stu-id="96227-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="96227-174">Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównane do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="96227-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="96227-175">Jeśli jest to liczba ujemna, pole jest wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="96227-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="96227-176">Spróbuj usunąć znaki ujemne z `{"Author",-25}` kodu i `{title.Key,-25}` i ponownie uruchomić przykład, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="96227-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="96227-177">Tym razem informacje o autorze są wyrównane do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="96227-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="96227-178">Można połączyć specyfikator wyrównania i ciąg formatu dla pojedynczego wyrażenia interpolacji.</span><span class="sxs-lookup"><span data-stu-id="96227-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="96227-179">W tym celu należy określić wyrównania jako pierwsze, po którym następuje dwukropek i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="96227-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="96227-180">Zamień cały kod wewnątrz `Main` metody na następujący kod, który wyświetla trzy sformatowane ciągi ze zdefiniowanymi szerokościami pól.</span><span class="sxs-lookup"><span data-stu-id="96227-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="96227-181">Następnie uruchom program, wprowadzając `dotnet run` polecenie.</span><span class="sxs-lookup"><span data-stu-id="96227-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="96227-182">Dane wyjściowe wyglądają podobnie do następujących:</span><span class="sxs-lookup"><span data-stu-id="96227-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="96227-183">Samouczek interpolacji ciągów został ukończony.</span><span class="sxs-lookup"><span data-stu-id="96227-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="96227-184">Aby uzyskać więcej informacji, zobacz temat [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) i [ C# Interpolacja ciągów w](../../tutorials/string-interpolation.md) samouczku.</span><span class="sxs-lookup"><span data-stu-id="96227-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
