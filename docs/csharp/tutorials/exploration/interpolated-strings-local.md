---
title: Interpolacja ciągów — samouczek C#
description: W tym samouczku pokazano, jak używać funkcji interpolacji ciągów języka C#, aby uwzględnić sformatowane wyniki wyrażenia w większym ciągu.
ms.date: 10/23/2018
ms.openlocfilehash: 22637895f241585bac4909479f225bf3cb581614
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738283"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Używanie interpolacji ciągów do konstruowania sformatowanych ciągów

W tym samouczku opisano, jak używać [interpolacji ciągów](../../language-reference/tokens/interpolated.md) języka C#, aby wstawić wartości do pojedynczego ciągu wynikowego. Piszesz kod C# i widzisz wyniki kompilacji i uruchamiania go. Samouczek zawiera serię lekcji, które pokazują, jak wstawić wartości do ciągu i sformatować te wartości na różne sposoby.

W tym samouczku oczekuje, że masz komputer, którego można użyć do tworzenia. W samouczku .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) są instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemach Windows, Linux lub macOS. Można również ukończyć [interaktywną wersję](interpolated-strings.yml) tego samouczka w przeglądarce.

## <a name="create-an-interpolated-string"></a>Tworzenie ciągu interpolowanego

Utwórz katalog o nazwie *interpolowany*. Spraw, aby był to bieżący katalog i uruchom następujące polecenie z okna konsoli:

```dotnetcli
dotnet new console
```

To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.

Otwórz *Program.cs* w ulubionym edytorze i zastąp wiersz `Console.WriteLine("Hello World!");` następującym `<name>` kodem, w którym zastępujesz swoim imieniem i nazwiskiem:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Wypróbuj ten kod, `dotnet run` wpisując go w oknie konsoli. Kiedy uruchomisz program, zostanie wyświetlony jeden ciąg z Twoim imieniem w powitaniu. Ciąg zawarty w <xref:System.Console.WriteLine%2A> wywołaniu metody jest *interpolowanym wyrażeniem ciągu*. Jest to rodzaj szablonu, który umożliwia skonstruowanie pojedynczego ciągu (zwanego *ciągiem wynikowym*) z ciągu obejmującego osadzony kod. Ciągi interpolowane są szczególnie użyteczne do wstawiania wartości do ciągu lub łączenia ciągów.

Ten prosty przykład zawiera dwa elementy, które musi mieć każdy ciąg interpolowany:

- Literał ciągu rozpoczynający się od znaku `$` przed otwierającym znakiem cudzysłowu. Pomiędzy symbolem `$` i znakiem zapytania nie może być żadnych odstępów. (Jeśli chcesz zobaczyć, co się stanie, jeśli go dodasz, wstaw spację po `$` znaku, `dotnet run` zapisz plik i uruchom program ponownie, wpisując go w oknie konsoli. Kompilator języka C# wyświetla komunikat o błędzie "error CS1056: Unexpected character '$'".)

- Jedno lub więcej *wyrażeń interpolacji*. Wyrażenie interpolacji jest wskazywane przez nawias`{` `}`otwierający i zamykający ( i ). Do nawiasów klamrowych możesz wstawić dowolne wyrażenie języka C# zwracające wartość (w tym `null`).

Wypróbujmy kilka przykładów interpolacji ciągów z innymi typami danych.

## <a name="include-different-data-types"></a>Uwzględnianie innych typów danych

W poprzedniej sekcji użyto interpolacji ciągu, aby wstawić jeden ciąg wewnątrz drugiego. Wynik wyrażenia interpolacji może być dowolnego typu danych, choć. Uwzględnijmy wartości różnych typów danych w ciągu interpolowanym.

W poniższym przykładzie najpierw definiujemy `Vegetable` typ `Name` danych [klasy,](../../programming-guide/classes-and-structs/classes.md) który ma [właściwość](../../properties.md) `ToString` i <xref:System.Object.ToString?displayProperty=nameWithType> [metodę](../../methods.md), która [zastępuje](../../language-reference/keywords/override.md) zachowanie metody. [ `public` Modyfikator dostępu](../../language-reference/keywords/public.md) udostępnia tę metodę dowolnego kodu klienta, aby uzyskać reprezentację `Vegetable` ciągu wystąpienia. W przykładzie `Vegetable.ToString` metoda zwraca wartość `Name` właściwości, która jest `Vegetable` inicjowana w [konstruktorze:](../../programming-guide/classes-and-structs/constructors.md)

```csharp
public Vegetable(string name) => Name = name;
```

Następnie tworzymy wystąpienie `Vegetable` klasy `item` o nazwie przy użyciu [ `new` operatora](../../language-reference/operators/new-operator.md) i `Vegetable`podając nazwę konstruktora:

```csharp
var item = new Vegetable("eggplant");
```

Na koniec uwzględniamy `item` zmienną do interpolowanego ciągu, <xref:System.DateTime> który <xref:System.Decimal> zawiera również `Unit` wartość, wartość i wartość [wyliczenia.](../../language-reference/builtin-types/enum.md) Zastąp cały kod C# w edytorze następującym `dotnet run` kodem, a następnie użyj polecenia, aby go uruchomić:

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

Należy zauważyć, że `item` wyrażenie interpolacji w interpolowanym ciągu jest rozpoznawane jako tekst "bakłażan" w ciągu wynikowym. To dlatego, że gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest rozpoznawany do ciągu w następujący sposób:

- Jeśli wyrażenie interpolacji jest `null`oblicza, że używany <xref:System.String.Empty?displayProperty=nameWithType>jest pusty ciąg ("", lub ).

- Jeśli wyrażenie interpolacji nie ocenia `null`, zazwyczaj `ToString` wywoływana jest metoda typu wynikowego. Można to przetestować, aktualizując `Vegetable.ToString` implementację metody. Może nawet nie trzeba `ToString` zaimplementować metody, ponieważ każdy typ ma pewne implementacji tej metody. Aby to sprawdzić, należy skomentować definicję `Vegetable.ToString` metody w przykładzie (aby `//`to zrobić, umieść symbol komentarza, przed nim). W danych wyjściowych ciąg "bakłażan" jest zastępowany przez w pełni kwalifikowaną nazwę typu <xref:System.Object.ToString?displayProperty=nameWithType> ("Warzyw" w tym przykładzie), co jest domyślnym zachowaniem metody. Domyślnym zachowaniem `ToString` metody dla wartości wyliczenia jest zwrócenie reprezentacji ciągu wartości.

W danych wyjściowych z tego przykładu data jest zbyt dokładna (cena bakłażana nie zmienia się co sekundę), a wartość ceny nie wskazuje jednostki waluty. W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format reprezentacji ciągów wyników wyrażeń.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Sterowanie formatowaniem wyrażeń interpolacji

W poprzedniej sekcji dwa źle sformatowane ciągi zostały wstawione do ciągu wynikowego. Jednym z nich była wartość daty i godziny, chociaż tylko data powinna mieć zastosowanie. Druga to cena, która nie wskazywała jej jednostki waluty. Oba problemy można z łatwością rozwiązać. Interpolacja ciągów umożliwia określenie *ciągów formatu,* które kontrolują formatowanie określonych typów. Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby uwzględnić ciągi formatu dla wyrażeń daty i ceny, jak pokazano w następującym wierszu:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Ciąg formatu można określić, postępając zgodnie z wyrażeniem interpolacji z dwukropkiem (":") i ciągiem formatu. „d” jest [standardowym ciągiem formatu daty i godziny](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier), który reprezentuje krótki format daty. „C2” to [standardowy ciąg formatu numerycznego](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier), który reprezentuje liczbę jako wartość waluty z dwoma cyframi po separatorze dziesiętnym.

Wiele typów w bibliotekach platformy .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatu. Uwzględnia to wszystkie typy numeryczne oraz typy daty i godziny. Aby uzyskać kompletną listę typów, które obsługują ciągi formatu, zobacz [Ciągi formatu i typy biblioteki klas .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) w artykule [Typy formatowania na platformie .NET](../../../standard/base-types/formatting-types.md).

Spróbuj zmodyfikować ciągi formatu w edytorze tekstu i za każdym razem, gdy dokonasz zmiany, uruchom ponownie program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej. Zmień „d” w ciągu `{date:d}` na „t” (aby wyświetlić krótki format daty), „y” (aby wyświetlić rok i miesiąc) oraz „yyyy” (aby wyświetlać rok jako liczbę czterocyfrową). Zmień „C2” w ciągu `{price:C2}` na „e” (notacja wykładnicza) oraz „F3” (wartość numeryczna z trzema cyframi po separatorze dziesiętnym).

Oprócz kontrolowania formatowania można również kontrolować szerokość pola i wyrównanie sformatowanych ciągów ciągów, które są zawarte w ciągu wynikowym. W następnej sekcji dowiesz się, jak to zrobić.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Sterowanie szerokością pola i wyrównaniem wyrażeń interpolacji

Zwykle, gdy wynik wyrażenia interpolacji jest sformatowany do ciągu, ten ciąg jest zawarty w ciągu wynik bez spacji wiodących lub końcowych. Szczególnie podczas pracy z zestawem danych, możliwość kontrolowania szerokości pola i wyrównanie tekstu pomaga uzyskać bardziej czytelne dane wyjściowe. Aby to zobaczyć, zastąp cały kod w edytorze tekstu następującym kodem, a następnie wpisz, `dotnet run` aby wykonać program:

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

Nazwy autorów są wyrównane do lewej, a tytuły, które napisali, są wyrównane do prawej. Wyrównanie można określić, dodając przecinek (",") po wyrażeniu interpolacji i wyznaczając *minimalną* szerokość pola. Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównane do prawej. Jeśli jest to liczba ujemna, pole jest wyrównane do lewej.

Spróbuj usunąć znaki ujemne `{"Author",-25}` z `{title.Key,-25}` i kodu i uruchom przykład ponownie, jak następujący kod nie:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Tym razem informacje o autorze są wyrównane do prawej.

Można połączyć specyfikator wyrównania i ciąg formatu dla pojedynczego wyrażenia interpolacji. Aby to zrobić, należy najpierw określić wyrównanie, a następnie dwukropek i ciąg formatu. Zastąp cały `Main` kod wewnątrz metody następującym kodem, który wyświetla trzy sformatowane ciągi o zdefiniowanych szerokościach pól. Następnie uruchom program, wprowadzając `dotnet run` polecenie.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Dane wyjściowe wyglądają mniej więcej tak:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Ukończono samouczek interpolacji ciągów.

Aby uzyskać więcej informacji, zobacz [temat interpolacji ciągów](../../language-reference/tokens/interpolated.md) i [interpolacji ciągów w](../../tutorials/string-interpolation.md) samouczku C#.
