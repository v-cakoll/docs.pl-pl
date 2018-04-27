---
title: Samouczek interpolacji ciągu - C# lokalnego poradniki Szybki Start
description: Ta opcja szybkiego startu przedstawia zawiera wyrażenie sformatowane wyniki w większych ciągu przy użyciu funkcji interpolacji ciągu języka C#.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 7ef904e30475d2cc0584f2baf56bc33a68e172d4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="string-interpolation"></a>Ciąg interpolacji

Ta opcja szybkiego startu zawiera wskazówki, jak używać języka C# [ciągu interpolacji](../language-reference/tokens/interpolated.md) do wstawienia wartości na ciąg pojedynczego wyniku. Pisanie kodu C# i wyświetlić wyniki kompilowania i uruchamiania go. Procedury szybkiego startu zawiera szereg lekcje, które pokazują, jak wstawienia wartości do ciągu i sformatować te wartości na różne sposoby.

Ta opcja szybkiego startu oczekuje, że maszynie, która służy do tworzenia aplikacji. Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux. Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego poradniki Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów. Można też wykonać [wersji interaktywnego](interpolated-strings.yml) z tego przewodnika Szybki Start w przeglądarce.

## <a name="create-an-interpolated-string"></a>Tworzenie ciągu interpolowanym

Utwórz katalog o nazwie **interpolowane**. Stał się bieżący katalog i uruchom następujące polecenie z poziomu okna konsoli:

```console
dotnet new console
```

To polecenie tworzy nową aplikację konsolową .NET Core w bieżącym katalogu.

Otwórz **Program.cs** ulubionego edytora i Zastąp linię `Console.WriteLine("Hello World!");` z następującym kodem, gdzie Zastąp `<name>` nazwą:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Spróbuj ten kod, wpisując `dotnet run` w oknie konsoli. Po uruchomieniu program wyświetla jeden ciąg zawierający nazwę w pozdrowienie. Ciąg zawarty w <xref:System.Console.WriteLine%2A> jest wywołanie metody *interpolowane ciąg*. Jest to rodzaj szablonu, który pozwala utworzyć jeden ciąg (o nazwie *powoduje ciąg*) z ciągu, który zawiera osadzony kod. Ciągi interpolowane są szczególnie użyteczne w przypadku wstawiania wartości w ciągu lub ciągi łączenie (łączenie).

Ten prosty przykład zawiera dwa elementy, które muszą mieć co ciągu interpolowanym:

- Literał ciągu rozpoczynający się od `$` znak przed jego otwierania przez cudzysłów znaków. Nie może być odstępów między `$` symboli i znaku cudzysłowu. (Jeśli chcesz zobaczyć co się stanie w przypadku obejmują jeden, Wstaw spację po `$` znak, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli. Kompilator języka C# Wyświetla komunikat o błędzie "Błąd CS1056: nieoczekiwany znak"$"".)

- Co najmniej jeden *interpolowane wyrażenia*. Wskazuje wyrażenie interpolowane otwierający i zamykający nawias klamrowy (`{` i `}`). Możesz też zaznaczyć dowolne C# wyrażenie zwracające wartość (w tym `null`) w nawiasach klamrowych.

Poniżej przedstawiono kilka innych przykładów interpolacji ciągu z innych typów danych.

## <a name="include-different-data-types"></a>Obejmują różne typy danych

W poprzedniej sekcji interpolacji ciąg jest używany do wstawiania jeden ciąg wewnątrz innego. Wynik wyrażenia interpolowane może być jednak każdego typu danych. Załóżmy obejmują wartości różnych typów danych w ciągu interpolowanym.

W poniższym przykładzie najpierw definiujemy niestandardowego typu danych `Vegetable` mający `Name` [właściwości](../properties.md) i `ToString` metody. Kod klienta można użyć tej metody można uzyskać reprezentację ciągu `Vegetable` wystąpienia. W przykładzie `Vegetable.ToString` metoda zwraca wartość `Name` właściwość, która została zainicjowana w `Vegetable` konstruktora:

```csharp
public Vegetable(string name) => Name = name;
```

Utwórz wystąpienie `Vegetable` typu przy użyciu `new` — słowo kluczowe i podając nazwę parametru konstruktora `Vegetable`:

```csharp
var item = new Vegetable("eggplant");
```

Na koniec przeprowadzamy `item` zmiennej w ciągu interpolowanym zawierającej również <xref:System.DateTime> wartość, <xref:System.Decimal> wartości i `Unit` [wyliczenie](../programming-guide/enumeration-types.md) wartość. Zamień wszystkie kodu C# w Edytorze następujący kod, a następnie użyj `dotnet run` polecenie, aby uruchomić go:

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

Należy pamiętać, że interpolowanego wyrażenia `item` w ciągu interpolowanym jest rozpoznawana jako tekst "oberżynowego" w ciągu wynik. Wynika to, gdy typ wyniku wyrażenia nie jest ciągiem, wynik został rozwiązany na ciąg w następujący sposób:

- Jeśli interpolowanego wyrażenia `null`, ciąg pusty ("", lub <xref:System.String.Empty?displayProperty=nameWithType>) jest używany.

- Jeśli interpolowanego wyrażenia nie być `null`, zwykle `ToString` wywoływana jest metoda typu wyniku. Można to sprawdzić, aktualizując wykonania `Vegetable.ToString` metody. Być może nawet nie implementuje `ToString` metody, ponieważ niektóre implementacja tej metody ma wszystkie typy danych języka C#. Aby sprawdzić, czy, w komentarz definicję `Vegetable.ToString` metody w tym przykładzie (w tym celu umieść symbol komentarza `//` przed nim). W danych wyjściowych, ciąg "oberżynowego" zostanie zastąpiony przez w pełni kwalifikowaną nazwę typu ("roślinny" w tym przykładzie), który jest domyślnym zachowaniem z <xref:System.Object.ToString?displayProperty=nameWithType> metody. Domyślne zachowanie `ToString` metody dla typu wyliczenia jest zwraca reprezentację ciągu wartość używana w definicji wyliczenia.

W danych wyjściowych w tym przykładzie Data jest zbyt precyzyjna (cena oberżynowego nie zmienia co sekundę), a wartość ceny nie oznacza jednostkę waluty. W następnej sekcji dowiesz się, jak rozwiązać te problemy kontrolując formatu ciągu reprezentacje wyników wyrażenia.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Formant formatowanie interpolowanego wyrażenia

W poprzedniej sekcji nieprawidłowo sformatowany dwa ciągi, które zostały wstawione do ciągu wynik. Jeden jest wartość daty i godziny, dla którego został właściwe tylko data. Drugi był cenę nie wskazywać jego jednostkę waluty. Problemy z obu łatwych do adresu. Ciąg interpolacji umożliwia określenie *ciągi formatujące* umożliwiające sterowanie formatowanie poszczególnych typów. Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby uwzględnić ciągi formatujące datę i cenę wyrażeń, jak pokazano w następującym wierszu:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Podaj ciąg formatu, używając interpolowanego wyrażenia dwukropka (":"), a ciąg formatu. "d" jest [standardowa Data i godzina ciąg formatu](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) reprezentujący format daty krótkiej. "C2" jest [ciągu standardowego formatu liczbowego](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) reprezentujący liczbę jako wartość walutową z dwóch cyfr po punkcie dziesiętnym.

Liczba typów w bibliotek .NET obsługuje zestaw wstępnie zdefiniowanych ciągi formatów. Obejmuje to wszystkie typy liczbowe oraz typy daty i godziny. Pełną listę typów, które obsługują ciągi formatów, zobacz [ciągi formatów i typy biblioteki klas .NET](../../standard/base-types/formatting-types.md#stringRef) w [typy formatowania w .NET](../../standard/base-types/formatting-types.md) artykułu.

Spróbuj zmodyfikować ciągów formatu w edytorze tekstu i, za każdym razem, wprowadzić zmiany, ponownie uruchom program, aby zobaczyć wpływ zmian na format daty i godziny oraz wartość liczbową. Zmiana "d" `{date:d}` "t" (do wyświetlania na format godziny krótkiej), "y" (Aby wyświetlić rok i miesiąc), a "yyyy" (do wyświetlania roku w postaci czterech cyfr). Zmiana "C2" `{price:C2}` "e" (w notacji wykładniczej) i "F3" (dla wartość liczbową z trzech cyfr po punkcie dziesiętnym).

Oprócz kontrolowanie formatowania, można też kontrolować szerokość pola i wyrównanie sformatowany ciągów, które znajdują się w ciągu wynik. W następnej sekcji dowiesz się, jak to zrobić.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Szerokość pola i wyrównanie interpolowanego wyrażenia

Zwykle podczas formatowania wynik wyrażenia interpolowane na ciąg, ten ciąg znajduje się w ciągu wynik bez początkowe lub końcowe spacje. Szczególnie podczas pracy z zestawem danych, możliwość kontrolowania szerokość pola i pomaga wyrównanie tekstu, aby wygenerować bardziej czytelny dane wyjściowe. Aby wyświetlić to Zastąp następujący kod całego kodu w edytorze tekstu, następnie wpisz `dotnet run` do wykonania programu:

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

Nazwy autorów są wyrównane do lewej, a tytułów, które są napisane są wyrównane do lewej. Określ wyrównanie przez dodanie przecinka (",") po interpolowanego wyrażenia i wyznaczające *minimalna* szerokości pola. Jeśli określona wartość jest liczbą dodatnią, to pole jest wyrównany do prawej. Jeśli jest liczbą ujemną, to pole jest wyrównane do lewej.

Spróbuj usunąć ujemna znaki z `{"Author",-25}` i `{title.Key,-25}` kodu i ponownie uruchomić przykład, tak jak w następującym kodem:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Teraz, informacje o autorze jest wyrównany do prawej.

Specyfikator wyrównania i ciągu formatu dla pojedynczego wyrażenia interpolowane można łączyć. W tym celu Określ wyrównanie najpierw następuje dwukropek i ciąg formatu. Zamień wszystkie kodu wewnątrz `Main` metodę z następującym kodem, która zawiera trzy ciągi sformatowane z zdefiniowane szerokości pól. Następnie uruchom program wprowadzając `dotnet run` polecenia.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Dane wyjściowe podobne następujące czynności:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Zakończono szybkiego startu interpolacji ciągu.

Można kontynuować [listy kolekcji](arrays-and-collections.md) szybkiego startu w środowisku projektowania.

Dowiedz się więcej o interpolacji ciągu w [ciągu interpolacji](../language-reference/tokens/interpolated.md) tematu w odwołanie w C#.
