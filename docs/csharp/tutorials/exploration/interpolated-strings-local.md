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
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Używanie interpolacji ciągów do konstruowania sformatowanych ciągów

W tym samouczku nauczy cię, jak używać [interpolacji ciągów](../../language-reference/tokens/interpolated.md) C# do wstawiania wartości do jednego ciągu wynikowego. Piszesz kod C# i zobaczyć wyniki kompilacji i uruchamiania go. Samouczek zawiera serię lekcji, które pokazują, jak wstawić wartości do ciągu i sformatować te wartości na różne sposoby.

Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia. Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS. Możesz również ukończyć [interaktywną wersję](interpolated-strings.yml) tego samouczka w przeglądarce.

## <a name="create-an-interpolated-string"></a>Tworzenie ciągu interpolowanego

Utwórz katalog o nazwie *interpolowany*. Uczyń go bieżącym katalogiem i uruchom następujące polecenie z okna konsoli:

```dotnetcli
dotnet new console
```

To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.

Otwórz *Program.cs* w ulubionym edytorze `Console.WriteLine("Hello World!");` i zastąp wiersz `<name>` następującym kodem, w którym możesz zastąpić swoje imię i nazwisko:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Wypróbuj `dotnet run` ten kod, wpisując w oknie konsoli. Kiedy uruchomisz program, zostanie wyświetlony jeden ciąg z Twoim imieniem w powitaniu. Ciąg zawarty <xref:System.Console.WriteLine%2A> w wywołaniu metody jest *interpolowanym wyrażeniem ciągu*. Jest to rodzaj szablonu, który umożliwia skonstruowanie pojedynczego ciągu (zwanego *ciągiem wynikowym*) z ciągu obejmującego osadzony kod. Ciągi interpolowane są szczególnie użyteczne do wstawiania wartości do ciągu lub łączenia ciągów.

Ten prosty przykład zawiera dwa elementy, które musi mieć każdy ciąg interpolowany:

- Literał ciągu rozpoczynający się od znaku `$` przed otwierającym znakiem cudzysłowu. Pomiędzy symbolem `$` i znakiem zapytania nie może być żadnych odstępów. (Jeśli chcesz zobaczyć, co się stanie, jeśli go dodasz, wstaw spacja po `$` znaku, `dotnet run` zapisz plik i uruchom program ponownie, wpisując go w oknie konsoli. Kompilator C# wyświetla komunikat o błędzie "błąd CS1056: Nieoczekiwany znak '$'".)

- Jedno lub więcej *wyrażeń interpolacji*. Wyrażenie interpolacji jest oznaczone nawiasem klamrowym otwierania i zamykania (`{` i `}`). Do nawiasów klamrowych możesz wstawić dowolne wyrażenie języka C# zwracające wartość (w tym `null`).

Spróbujmy kilka przykładów interpolacji ciągów z niektórych innych typów danych.

## <a name="include-different-data-types"></a>Uwzględnianie innych typów danych

W poprzedniej sekcji użyto interpolacji ciągów, aby wstawić jeden ciąg wewnątrz innego. Wynik wyrażenia interpolacji może być dowolnego typu danych, choć. Uwzględnijmy wartości różnych typów danych w interpolowanym ciągu.

W poniższym przykładzie najpierw definiujemy `Vegetable` typ danych `Name` [klasy,](../../programming-guide/classes-and-structs/classes.md) który ma [właściwość](../../properties.md) i `ToString` <xref:System.Object.ToString?displayProperty=nameWithType> [metodę](../../methods.md), która [zastępuje](../../language-reference/keywords/override.md) zachowanie metody. [ `public` Modyfikator dostępu](../../language-reference/keywords/public.md) udostępnia tę metodę do dowolnego kodu `Vegetable` klienta, aby uzyskać reprezentację ciągu wystąpienia. W przykładzie `Vegetable.ToString` metoda zwraca wartość `Name` właściwości, która jest `Vegetable` inicjowana w [konstruktorze:](../../programming-guide/classes-and-structs/constructors.md)

```csharp
public Vegetable(string name) => Name = name;
```

Następnie tworzymy wystąpienie `Vegetable` klasy `item` o nazwie przy użyciu [ `new` operatora](../../language-reference/operators/new-operator.md) i podając nazwę dla konstruktora: `Vegetable`

```csharp
var item = new Vegetable("eggplant");
```

Na koniec możemy `item` dołączyć zmienną do interpolowany <xref:System.DateTime> ciąg, <xref:System.Decimal> który zawiera `Unit` również wartość, wartość i wartość [wyliczenia.](../../language-reference/builtin-types/enum.md) Zastąp cały kod Języka C# w edytorze `dotnet run` następującym kodem, a następnie użyj polecenia, aby go uruchomić:

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

Należy zauważyć, że `item` wyrażenie interpolacji w interpolowanym ciągu jest rozpoznawane z tekstem "bakłażan" w ciągu wynikowym. Dzieje się tak, ponieważ gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest rozpoznawany do ciągu w następujący sposób:

- Jeśli wyrażenie interpolacji jest `null`oceniane , jest używany <xref:System.String.Empty?displayProperty=nameWithType>pusty ciąg ("", lub ) .

- Jeśli wyrażenie interpolacji nie ocenia `null`, zazwyczaj `ToString` nazywa się metodę typu wynikowego. Można to przetestować, aktualizując `Vegetable.ToString` implementację metody. Może nawet nie trzeba `ToString` zaimplementować metodę, ponieważ każdy typ ma implementację tej metody. Aby to przetestować, skomentuj `Vegetable.ToString` definicję metody w przykładzie (aby to `//`zrobić, umieść symbol komentarza, przed nim). W danych wyjściowych ciąg "bakłażan" jest zastępowany w pełni kwalifikowaną nazwą typu ("Warzywo" w tym przykładzie), która jest domyślnym zachowaniem <xref:System.Object.ToString?displayProperty=nameWithType> metody. Domyślnym zachowaniem `ToString` metody dla wartości wyliczenia jest zwrócenie reprezentacji ciągu wartości.

W danych wyjściowych z tego przykładu data jest zbyt precyzyjna (cena bakłażana nie zmienia się co sekundę), a wartość ceny nie wskazuje jednostki waluty. W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format reprezentacji ciągów wyników wyrażenia.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Sterowanie formatowaniem wyrażeń interpolacji

W poprzedniej sekcji dwa źle sformatowane ciągi zostały wstawione do ciągu wynikowego. Jednym z nich była wartość daty i godziny, chociaż tylko data powinna mieć zastosowanie. Druga to cena, która nie wskazywała na jednostkę waluty. Oba problemy można z łatwością rozwiązać. Interpolacja ciągów umożliwia określenie *formatów,* które kontrolują formatowanie określonych typów. Zmodyfikuj wywołanie z poprzedniego przykładu, aby `Console.WriteLine` uwzględnić ciągi formatu dla wyrażeń daty i ceny, jak pokazano w następującym wierszu:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Ciąg formatu można określić, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągiem formatu. „d” jest [standardowym ciągiem formatu daty i godziny](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), który reprezentuje krótki format daty. „C2” to [standardowy ciąg formatu numerycznego](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), który reprezentuje liczbę jako wartość waluty z dwoma cyframi po separatorze dziesiętnym.

Wiele typów w bibliotekach .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatu. Uwzględnia to wszystkie typy numeryczne oraz typy daty i godziny. Aby uzyskać kompletną listę typów, które obsługują ciągi formatu, zobacz [Ciągi formatu i typy biblioteki klas .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) w artykule [Typy formatowania na platformie .NET](../../../standard/base-types/formatting-types.md).

Spróbuj zmodyfikować ciągi formatu w edytorze tekstu i za każdym razem, gdy wprowadzasz zmianę, uruchom ponownie program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej. Zmień „d” w ciągu `{date:d}` na „t” (aby wyświetlić krótki format daty), „y” (aby wyświetlić rok i miesiąc) oraz „yyyy” (aby wyświetlać rok jako liczbę czterocyfrową). Zmień „C2” w ciągu `{price:C2}` na „e” (notacja wykładnicza) oraz „F3” (wartość numeryczna z trzema cyframi po separatorze dziesiętnym).

Oprócz sterowania formatowaniem można również sterować szerokością pola i wyrównaniem sformatowanych ciągów, które są zawarte w ciągu wyników. W następnej sekcji dowiesz się, jak to zrobić.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Sterowanie szerokością pola i wyrównaniem wyrażeń interpolacji

Zwykle, gdy wynik wyrażenia interpolacji jest sformatowany na ciąg, ten ciąg jest dołączony do ciągu wynikowego bez spacji wiodących lub końcowych. Szczególnie podczas pracy z zestawem danych, możliwość kontrolowania szerokości pola i wyrównania tekstu pomaga uzyskać bardziej czytelne dane wyjściowe. Aby to zobaczyć, zamień cały kod w edytorze `dotnet run` tekstu następującym kodem, a następnie wpisz, aby wykonać program:

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

Nazwiska autorów są wyrównane do lewej, a tytuły, które napisali, są wyrównane do prawej. Wyrównanie należy określić, dodając przecinek (",") po wyrażeniu interpolacji i wyznaczając *minimalną* szerokość pola. Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównane do prawej. Jeśli jest to liczba ujemna, pole jest wyrównane do lewej.

Spróbuj usunąć znaki ujemne z `{"Author",-25}` kodu i `{title.Key,-25}` ponownie uruchomić przykład, jak to robi następujący kod:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Tym razem informacje autora są wyrównane do prawej.

Można połączyć specyfikator wyrównania i ciąg formatu dla pojedynczego wyrażenia interpolacji. Aby to zrobić, najpierw określ wyrównanie, a następnie dwukropek i ciąg formatu. Zamień cały kod `Main` wewnątrz metody na następujący kod, który wyświetla trzy sformatowane ciągi o zdefiniowanych szerokościach pól. Następnie uruchom program, wprowadzając `dotnet run` polecenie.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Dane wyjściowe wyglądają mniej więcej tak:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Ukończono samouczek interpolacji ciągu.

Aby uzyskać więcej informacji, zobacz [temat Interpolacji ciąg](../../language-reference/tokens/interpolated.md) ów i [Interpolacji ciąg w języku C#tutorial.](../../tutorials/string-interpolation.md)
