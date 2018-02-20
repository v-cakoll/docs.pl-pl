---
title: "Ciągi interpolowane samouczek - C# lokalnego poradniki Szybki Start"
description: "W tym Szybki Start o ciągi interpolowane pisania kodu C# do obejmują wynik wyrażenia w większych ciągu."
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: b6089b69eb350fce29f86f19f5abeb44acb4b6b4
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="interpolated-strings"></a><span data-ttu-id="00a9a-103">Ciągi interpolowane</span><span class="sxs-lookup"><span data-stu-id="00a9a-103">Interpolated strings</span></span>

<span data-ttu-id="00a9a-104">Ta opcja szybkiego startu zawiera sposób użycia ciągi interpolowane w języku C# do wstawienia wartości do ciągu wyjściowego pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="00a9a-104">This quickstart teaches you how to use interpolated strings in C# to insert values into a single ouput string.</span></span> <span data-ttu-id="00a9a-105">Pisanie kodu C# i wyświetlić wyniki kompilowania i uruchamiania go.</span><span class="sxs-lookup"><span data-stu-id="00a9a-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="00a9a-106">Procedury szybkiego startu zawiera szereg lekcje, które wstawienia wartości do ciągów i sformatować te wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="00a9a-106">The quickstart contains a series of lessons that insert values into strings, and format those values in different ways.</span></span>

<span data-ttu-id="00a9a-107">Ta opcja szybkiego startu oczekuje, że maszynie, która służy do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00a9a-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="00a9a-108">Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux.</span><span class="sxs-lookup"><span data-stu-id="00a9a-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="00a9a-109">Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego poradniki Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="00a9a-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> 

## <a name="create-an-interpolated-string"></a><span data-ttu-id="00a9a-110">Tworzenie ciągu interpolowanym</span><span class="sxs-lookup"><span data-stu-id="00a9a-110">Create an interpolated string</span></span>

<span data-ttu-id="00a9a-111">Utwórz katalog o nazwie **interpolowane szybkiego startu**.</span><span class="sxs-lookup"><span data-stu-id="00a9a-111">Create a directory named **interpolated-quickstart**.</span></span> <span data-ttu-id="00a9a-112">Stał się bieżący katalog i uruchom następujące polecenie z poziomu okna konsoli:</span><span class="sxs-lookup"><span data-stu-id="00a9a-112">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console -n interpolated -o .
```

<span data-ttu-id="00a9a-113">To polecenie tworzy nową aplikację konsolową .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="00a9a-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="00a9a-114">Otwórz **Program.cs** ulubionego edytora i Zastąp linię `Console.WriteLine("Hello World!");` z następującym kodem, gdzie Zastąp `<name>` nazwą:</span><span class="sxs-lookup"><span data-stu-id="00a9a-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
<span data-ttu-id="00a9a-115">Spróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="00a9a-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="00a9a-116">Po uruchomieniu program wyświetla jeden ciąg zawierający nazwę w pozdrowienie.</span><span class="sxs-lookup"><span data-stu-id="00a9a-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="00a9a-117">Ciąg zawarty w <xref:System.Console.WriteLine%2A> jest wywołanie metody *interpolowane ciąg*.</span><span class="sxs-lookup"><span data-stu-id="00a9a-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="00a9a-118">Jest to rodzaj szablonu, który pozwala utworzyć jeden ciąg (o nazwie *powoduje ciąg*) z ciągu, który zawiera osadzony kod.</span><span class="sxs-lookup"><span data-stu-id="00a9a-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="00a9a-119">Ciągi interpolowane są szczególnie użyteczne w przypadku wstawiania wartości w ciągu lub ciągi łączenie (łączenie).</span><span class="sxs-lookup"><span data-stu-id="00a9a-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span> 
    
<span data-ttu-id="00a9a-120">Ten prosty przykład zawiera dwa elementy, które muszą mieć co ciągu interpolowanym:</span><span class="sxs-lookup"><span data-stu-id="00a9a-120">This simple example contains the two elements that every interpolated string must have:</span></span> 

- <span data-ttu-id="00a9a-121">Literał ciągu rozpoczynający się od `$` znak przed jego otwierania przez cudzysłów znaków.</span><span class="sxs-lookup"><span data-stu-id="00a9a-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="00a9a-122">Nie może być odstępów między `$` symboli i znaku cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="00a9a-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="00a9a-123">(Jeśli chcesz zobaczyć co się stanie w przypadku obejmują jeden, Wstaw spację po `$` znak, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="00a9a-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="00a9a-124">Kompilator języka C# Wyświetla komunikat o błędzie "Błąd CS1056: nieoczekiwany znak"$"".)</span><span class="sxs-lookup"><span data-stu-id="00a9a-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span> 

- <span data-ttu-id="00a9a-125">Co najmniej jeden *interpolowane wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="00a9a-125">One or more *interpolated expressions*.</span></span> <span data-ttu-id="00a9a-126">Wskazuje wyrażenie interpolowane otwierający i zamykający nawias klamrowy (`{` i `}`).</span><span class="sxs-lookup"><span data-stu-id="00a9a-126">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="00a9a-127">Możesz też zaznaczyć dowolne C# wyrażenie zwracające wartość (w tym `null`) w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="00a9a-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span> 

<span data-ttu-id="00a9a-128">Poniżej przedstawiono kilka przykładów z ciągu więcej interpolowane z innych typów danych.</span><span class="sxs-lookup"><span data-stu-id="00a9a-128">Let's try a few more interpolated string examples with some other data types.</span></span>
    
## <a name="include-different-data-types"></a><span data-ttu-id="00a9a-129">Obejmują różne typy danych</span><span class="sxs-lookup"><span data-stu-id="00a9a-129">Include different data types</span></span>

<span data-ttu-id="00a9a-130">W poprzedniej sekcji ciągu interpolowanym jest używany do wstawiania jeden ciąg wewnątrz innego.</span><span class="sxs-lookup"><span data-stu-id="00a9a-130">In the previous section, you used an interpolated string to insert one string inside of another.</span></span> <span data-ttu-id="00a9a-131">Wyrażenie ciągu interpolowanym mogą być dowolnego typu danych, mimo że.</span><span class="sxs-lookup"><span data-stu-id="00a9a-131">An interpolated string expression can be any data type, though.</span></span> <span data-ttu-id="00a9a-132">Spróbujmy ciągu interpolowanym zawierającego wartości wiele typów danych.</span><span class="sxs-lookup"><span data-stu-id="00a9a-132">Let's try an interpolated string that has values of multiple data types.</span></span> 
    
<span data-ttu-id="00a9a-133">Poniższy przykład zawiera interpolowanego wyrażenia z `Vegetable` obiektu, jest członkiem `Unit` wyliczenia, <xref:System.DateTime> wartości, a <xref:System.Decimal> wartość.</span><span class="sxs-lookup"><span data-stu-id="00a9a-133">The following example includes interpolated expressions with a `Vegetable` object, a member of the `Unit` enumeration, a <xref:System.DateTime> value, and a <xref:System.Decimal> value.</span></span> <span data-ttu-id="00a9a-134">Zamień wszystkie kodu C# w Edytorze następujący kod, a następnie użyj `console run` polecenie, aby uruchomić go:</span><span class="sxs-lookup"><span data-stu-id="00a9a-134">Replace all of the C# code in your editor with the following code, and then use the `console run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
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
    
<span data-ttu-id="00a9a-135">Należy pamiętać, że druga interpolowane wyrażenie zawiera `item` obiektów w ciągu wynik, który jest wyświetlany w konsoli, a w tym przypadku ciągu "oberżynowego" jest umieszczona w ciągu wynik.</span><span class="sxs-lookup"><span data-stu-id="00a9a-135">Note that the second interpolated expression includes the `item` object in the result string that's displayed to the console, and in this case the string "eggplant" is inserted into the result string.</span></span> <span data-ttu-id="00a9a-136">To znaczy, ponieważ typ interpolowanego wyrażenia nie jest ciągiem, kompilator języka C# wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="00a9a-136">That's because, when the type of an interpolated expression is not a string, the C# compiler does the following:</span></span>

- <span data-ttu-id="00a9a-137">Jeśli jest interpolowanego wyrażenia `null`, interpolowane wyrażenie zwraca ciąg pusty ("", lub <xref:System.String.Empty?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="00a9a-137">If the interpolated expression is `null`, the interpolated expression returns an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>).</span></span>

- <span data-ttu-id="00a9a-138">Jeśli interpolowanego wyrażenia nie jest `null`, `ToString` wywoływana jest metoda typu interpolowanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="00a9a-138">If the interpolated expression is not `null`, the `ToString` method of the type of the interpolated expression is called.</span></span> <span data-ttu-id="00a9a-139">Można to sprawdzić przez komentowania limit definicji `Vegetable.ToString` metody w tym przykładzie, umieszczając symbol komentarza (`//`) przed nim.</span><span class="sxs-lookup"><span data-stu-id="00a9a-139">You can test this by commenting out the definition of the `Vegetable.ToString` method in the example by putting a comment symbol (`//`) in front of it.</span></span> <span data-ttu-id="00a9a-140">W danych wyjściowych, ciąg "oberżynowego" zostanie zastąpiony przez typ nazwa, "Materiałem", która jest domyślne zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="00a9a-140">In the output, the string "eggplant" is replaced by the type name, "Vegetable", which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span>   

<span data-ttu-id="00a9a-141">W danych wyjściowych w tym przykładzie Data jest zbyt precyzyjna (cena oberżynowego nie różnią się zależnie od drugiego), a wartość ceny nie oznacza jednostkę waluty.</span><span class="sxs-lookup"><span data-stu-id="00a9a-141">In the output from this example, the date is too precise (the price of eggplant does not vary by the second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="00a9a-142">W następnej sekcji dowiesz się, jak rozwiązać te problemy kontrolując format ciągów zwrócony przez interpolowanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="00a9a-142">In the next section, you'll learn how to fix those issues by controlling the format of strings returned by interpolated expressions.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="00a9a-143">Formant formatowanie interpolowanego wyrażenia</span><span class="sxs-lookup"><span data-stu-id="00a9a-143">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="00a9a-144">W poprzedniej sekcji nieprawidłowo sformatowany dwa ciągi, które zostały wstawione do ciągu wynik.</span><span class="sxs-lookup"><span data-stu-id="00a9a-144">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="00a9a-145">Jeden jest wartość daty i godziny, dla którego został właściwe tylko data.</span><span class="sxs-lookup"><span data-stu-id="00a9a-145">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="00a9a-146">Drugi był cen, który nie poinformował jego jednostkę waluty.</span><span class="sxs-lookup"><span data-stu-id="00a9a-146">The second was a price that did not indicate its unit of currency.</span></span> <span data-ttu-id="00a9a-147">Problemy z obu łatwych do adresu.</span><span class="sxs-lookup"><span data-stu-id="00a9a-147">Both issues are easy to address.</span></span> <span data-ttu-id="00a9a-148">Interpolowanego wyrażenia mogą zawierać *ciągi formatujące* umożliwiające sterowanie formatowanie poszczególnych typów.</span><span class="sxs-lookup"><span data-stu-id="00a9a-148">Interpolated expressions can include *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="00a9a-149">Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby uwzględnić specyfikator formatu dla pól daty i cen, jak pokazano w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="00a9a-149">Modify the call to `Console.WriteLine` from the previous example to include the format specifier for the date and price fields as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
<span data-ttu-id="00a9a-150">Podaj ciąg formatu, używając interpolowanego wyrażenia dwukropek i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="00a9a-150">You specify a format string by following the interpolated expression with a colon and the format string.</span></span> <span data-ttu-id="00a9a-151">"d" jest [standardowa Data i godzina ciąg formatu](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) reprezentujący format daty krótkiej.</span><span class="sxs-lookup"><span data-stu-id="00a9a-151">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="00a9a-152">"C2" jest [ciągu standardowego formatu liczbowego](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) reprezentujący liczbę jako wartość walutową z dwóch cyfr po punkcie dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="00a9a-152">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="00a9a-153">Liczba typów w bibliotek .NET Standard obsługuje zestaw wstępnie zdefiniowanych ciągi formatów.</span><span class="sxs-lookup"><span data-stu-id="00a9a-153">A number of types in the .NET Standard libraries support a predefined set of format strings.</span></span> <span data-ttu-id="00a9a-154">Obejmuje to wszystkie typy liczbowe oraz typy daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="00a9a-154">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="00a9a-155">Pełną listę typów, które obsługują ciągi formatów, zobacz [ciągi formatów i typy biblioteki klas .NET](../../standard/base-types/formatting-types.md#stringRef) w [typy formatowania w .NET](../../standard/base-types/formatting-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="00a9a-155">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span> <span data-ttu-id="00a9a-156">Dowolny typ może obsługiwać zestaw ciągi formatów i można również tworzyć niestandardowych rozszerzeń formatowania, które zapewniają niestandardowe formatowanie dla istniejących typów.</span><span class="sxs-lookup"><span data-stu-id="00a9a-156">Any type can support a set of format strings, and you can also develop custom formatting extensions that provide custom formatting for existing types.</span></span> <span data-ttu-id="00a9a-157">Aby uzyskać informacje dotyczące formatowania niestandardowego, zapewniając <xref:System.ICustomFormatter> wdrażania, zobacz [niestandardowe formatowanie ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) w [typy formatowania w .NET](../../standard/base-types/formatting-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="00a9a-157">For information on custom formatting by providing an <xref:System.ICustomFormatter> implementation, see [Custom Formatting with ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="00a9a-158">Spróbuj zmodyfikować ciągów formatu w edytorze tekstu i, za każdym razem, wprowadzić zmiany, ponownie uruchom program, aby zobaczyć wpływ zmian na format daty i godziny oraz wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="00a9a-158">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="00a9a-159">Zmiana "d" `{date:d}` "t" (do wyświetlania na format godziny krótkiej), "y" (Aby wyświetlić rok i miesiąc), a "yyyy" (do wyświetlania roku w postaci czterech cyfr).</span><span class="sxs-lookup"><span data-stu-id="00a9a-159">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="00a9a-160">Zmiana "C2" `{price:C2}` "e" (w notacji wykładniczej) i "F3" (dla wartość liczbową z trzech cyfr po punkcie dziesiętnym).</span><span class="sxs-lookup"><span data-stu-id="00a9a-160">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="00a9a-161">Oprócz kontrolowanie formatowania, można też kontrolować pola szerokości i wyrównania ciągów zwrócony przez interpolowanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="00a9a-161">In addition to controlling formatting, you can also control the field width and alignment of the strings returned by an interpolated expression.</span></span> <span data-ttu-id="00a9a-162">W następnej sekcji dowiesz się, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="00a9a-162">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="00a9a-163">Szerokość pola i wyrównanie interpolowanego wyrażenia</span><span class="sxs-lookup"><span data-stu-id="00a9a-163">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="00a9a-164">Zwykle gdy długość ciągu zwróconego przez wyrażenie interpolowane znajduje się w ciągu wynik, ma bez spacji wiodących lub końcowych.</span><span class="sxs-lookup"><span data-stu-id="00a9a-164">Ordinarily, when the string returned by an interpolated expression is included in a result string, it has no leading or trailing spaces.</span></span> <span data-ttu-id="00a9a-165">Szczególnie w przypadku wystąpienia, w których użytkownik pracuje z zestawu danych, interpolowanego wyrażenia pozwalają określić szerokość pola i jego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="00a9a-165">Particularly for instances in which you are working with a set of data, interpolated expressions let you specify a field width and its alignment.</span></span> <span data-ttu-id="00a9a-166">Aby wyświetlić to Zastąp następujący kod całego kodu w edytorze tekstu, następnie wpisz `console run` do wykonania programu:</span><span class="sxs-lookup"><span data-stu-id="00a9a-166">To see this, replace all the code in your text editor with the following code, then type `console run` to execute the program:</span></span>
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
<span data-ttu-id="00a9a-167">Nazwy autorów są wyrównane do lewej, a tytułów, które są napisane są wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="00a9a-167">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="00a9a-168">Określ wyrównanie przez dodanie przecinka (",") po wyrażeniu i wyznaczające szerokości pola.</span><span class="sxs-lookup"><span data-stu-id="00a9a-168">You specify the alignment by adding a comma (",") after the expression and designating the field width.</span></span> <span data-ttu-id="00a9a-169">Jeśli szerokość pola jest dodatnia, pole jest wyrównany do prawej:</span><span class="sxs-lookup"><span data-stu-id="00a9a-169">If the field width is a positive number, the field is right-aligned:</span></span>

```text
{expression, width}
```

<span data-ttu-id="00a9a-170">Jeśli szerokość pola jest liczbą ujemną, pole jest wyrównane do lewej:</span><span class="sxs-lookup"><span data-stu-id="00a9a-170">If the field width is a negative number, the field is left-aligned:</span></span>

```text
{expression, -width}
```

<span data-ttu-id="00a9a-171">Spróbuj usunąć ujemna znaki z `{"Author",-25}` i `{title.Key,-25}` interpolowane wyrażeń i ponownie uruchomić przykład, tak jak w następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="00a9a-171">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` interpolated expressions and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"\n{"Author",25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,25}     {title.Value,30}");
```

<span data-ttu-id="00a9a-172">Teraz, informacje o autorze jest wyrównany do prawej.</span><span class="sxs-lookup"><span data-stu-id="00a9a-172">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="00a9a-173">Szerokość pola i ciąg formatu w jednym wyrażeniu interpolowane można łączyć.</span><span class="sxs-lookup"><span data-stu-id="00a9a-173">You can combine a field width and a format string in a single interpolated expression.</span></span> <span data-ttu-id="00a9a-174">Szerokość pola zostanie osiągnięty jako pierwszy, następuje dwukropek i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="00a9a-174">The field width comes first, followed by a colon and the format string.</span></span> <span data-ttu-id="00a9a-175">Zamień wszystkie kodu wewnątrz `Main` metodę z następującym kodem, która zawiera trzy ciągi sformatowane z zdefiniowane szerokości pól.</span><span class="sxs-lookup"><span data-stu-id="00a9a-175">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="00a9a-176">Następnie uruchom program wprowadzając `dotnet run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="00a9a-176">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
<span data-ttu-id="00a9a-177">Dane wyjściowe podobne następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="00a9a-177">The output looks something like the following:</span></span>

```console
1/11/2018            Hour 09                1,063.34 feet
```

<span data-ttu-id="00a9a-178">Zakończono ciągi interpolowane — Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="00a9a-178">You've completed the interpolated strings quickstart.</span></span> 
    
<span data-ttu-id="00a9a-179">Można kontynuować [kolekcji i tablic](arrays-and-collections.md) szybkiego startu w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="00a9a-179">You can continue with the [Arrays and collections](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="00a9a-180">Dowiedz się więcej o pracy z ciągi interpolowane w [ciągi interpolowane](../language-reference/keywords/interpolated-strings.md) tematu w odwołanie w C#.</span><span class="sxs-lookup"><span data-stu-id="00a9a-180">You can learn more about working with interpolated strings in the [Interpolated Strings](../language-reference/keywords/interpolated-strings.md) topic in the C# Reference.</span></span>

