---
title: Interpolacja ciągów — C# samouczek
description: W tym samouczku pokazano, jak za C# pomocą funkcji interpolacji ciągów dołączać sformatowane wyniki wyrażeń w większym ciągu.
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: 3e4e886d898854f5c1d966529e94f49c752220d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850926"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Użyj interpolacji ciągów, aby utworzyć sformatowane ciągi

W tym samouczku przedstawiono sposób użycia C# [interpolacji ciągu](../../language-reference/tokens/interpolated.md) do wstawiania wartości w postaci pojedynczego ciągu wynikowego. Napiszesz C# kod i zobaczysz wyniki kompilacji i uruchomienia. Samouczek zawiera serie lekcji pokazujące sposób wstawiania wartości do ciągu i formatowania tych wartości na różne sposoby.

Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania. Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego na komputerach Mac, komputerze lub Linux. Możesz również ukończyć [interaktywną wersję](interpolated-strings.yml) tego samouczka w przeglądarce.

## <a name="create-an-interpolated-string"></a>Utwórz ciąg interpolowany

Utwórz katalog o nazwie **interpolowane**. Ustaw jako bieżący katalog i uruchom następujące polecenie z okna konsoli:

```console
dotnet new console
```

To polecenie powoduje utworzenie nowej aplikacji konsolowej .NET Core w bieżącym katalogu.

Otwórz **program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem, w którym zastąpisz `<name>` swoją nazwę:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli. Po uruchomieniu programu w powitaniu zostanie wyświetlony pojedynczy ciąg zawierający nazwę użytkownika. Ciąg zawarty w <xref:System.Console.WriteLine%2A> wywołaniu metody jest *wyrażeniem ciągu interpolowanego*. Jest to rodzaj szablonu, który umożliwia konstruowanie pojedynczego ciągu (zwanego *ciągiem wynikowym*) z ciągu, który zawiera kod osadzony. Ciąg interpolowany jest szczególnie przydatny do wstawiania wartości do ciągu lub łączenia (łączenie ze sobą) ciągów.

Ten prosty przykład zawiera dwa elementy, które każdy ciąg interpolowany musi mieć:

- Literał ciągu zaczynający się od `$` znaku przed znakiem cudzysłowu otwierającego. Między `$` symbolem i znakiem cudzysłowu nie mogą znajdować się spacje. (Jeśli chcesz zobaczyć, co się stanie, jeśli dołączysz jeden, Wstaw spację po `$` znaku, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli. C# Kompilator wyświetla komunikat o błędzie "błąd CS1056: Nieoczekiwany znak "$" ".)

- Co najmniej jedno *wyrażenie interpolacji*. Wyrażenie interpolacji jest wskazywane przez otwierające i zamykające nawiasy`{` klamrowe (i `}`). Można umieścić dowolne C# Wyrażenie zwracające wartość (w tym `null`) w nawiasach klamrowych.

Wypróbujmy kilka przykładów interpolacji ciągów z innymi typami danych.

## <a name="include-different-data-types"></a>Uwzględnij różne typy danych

W poprzedniej sekcji użyto interpolacji ciągu do wstawienia jednego ciągu wewnątrz innego. Wynik wyrażenia interpolacji może być dowolnego typu danych, chociaż. Dołączmy wartości różnych typów danych w ciągu interpolowanym.

W poniższym przykładzie najpierw zdefiniujemy `Vegetable` typ danych [klasy](../../programming-guide/classes-and-structs/classes.md) , który ma `Name` [Właściwość](../../properties.md) i `ToString` [metodę](../../methods.md), która [zastępuje](../../language-reference/keywords/override.md) zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody. [ `public` Modyfikator dostępu](../../language-reference/keywords/public.md) sprawia, że ta metoda jest dostępna dla dowolnego kodu klienta, aby uzyskać `Vegetable` ciąg reprezentujący wystąpienie. W przykładzie `Vegetable.ToString` Metoda zwraca wartość `Name` właściwości `Vegetable` , która została zainicjowana w [konstruktorze](../../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Następnie `Vegetable` tworzymy wystąpienie klasy o `item` nazwie przy użyciu [ `new` operatora](../../language-reference/operators/new-operator.md) i dostarczając nazwę konstruktora: `Vegetable`

```csharp
var item = new Vegetable("eggplant");
```

Na `item` koniec dołączymy zmienną do ciągu interpolowanego, który <xref:System.DateTime> zawiera również wartość, <xref:System.Decimal> wartość i `Unit` wartość [wyliczenia](../../programming-guide/enumeration-types.md) . Zastąp cały C# kod w edytorze następującym kodem, a następnie użyj `dotnet run` polecenia, aby go uruchomić:

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

Należy zauważyć, że wyrażenie `item` interpolacji w ciągu interpolowanym jest rozpoznawane jako tekst "oberżyn" w ciągu wynikowym. Dzieje się tak, ponieważ, gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest rozpoznawany jako ciąg w następujący sposób:

- Jeśli wyrażenie interpolacji ma wartość `null`, jest używany pusty ciąg ("" lub <xref:System.String.Empty?displayProperty=nameWithType>).

- Jeśli wyrażenie interpolacji nie jest szacowane do `null`, `ToString` zazwyczaj wywoływana jest metoda typu wynik. Można to przetestować, aktualizując implementację `Vegetable.ToString` metody. Być może nie trzeba nawet implementować metody `ToString` , ponieważ każdy typ ma pewną implementację tej metody. Aby to przetestować, Dodaj komentarz do definicji `Vegetable.ToString` metody w przykładzie (w tym celu należy umieścić `//`symbol komentarza, przed nim). W danych wyjściowych ciąg "oberżyny" jest zamieniany przez w pełni kwalifikowaną nazwę typu ("warzywa" w tym przykładzie), która jest domyślnym zachowaniem <xref:System.Object.ToString?displayProperty=nameWithType> metody. Domyślnym zachowaniem `ToString` metody dla wartości wyliczenia jest zwrócenie ciągu reprezentującego wartość.

W danych wyjściowych tego przykładu Data jest zbyt dokładna (cena oberżyny nie zmienia się co sekundę), a wartość ceny nie wskazuje jednostki waluty. W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format wyników wyrażenia w postaci ciągów.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Sterowanie formatowaniem wyrażeń interpolacji

W poprzedniej sekcji dwa niewłaściwie sformatowane ciągi zostały wstawione do ciągu wynikowego. Jedna była wartością daty i godziny, dla której jest właściwa tylko Data. Druga cena była ceną, która nie wskazywała swojej jednostki waluty. Oba problemy są łatwe w obsłudze. Interpolacja ciągów pozwala określić *ciągi formatowania* , które kontrolują formatowanie poszczególnych typów. Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby uwzględnić ciągi formatu dla wyrażeń daty i ceny, jak pokazano w następującym wierszu:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Ciąg formatu można określić, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągiem formatu. "d" to [standardowy ciąg formatu daty i godziny](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) , który reprezentuje format daty krótkiej. "C2" to [standardowy ciąg formatu liczbowego](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) , który reprezentuje liczbę jako wartość walutową z dwiema cyframi po przecinku dziesiętnym.

Wiele typów w bibliotekach .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatujących. Obejmują one wszystkie typy liczbowe i typy daty i godziny. Aby zapoznać się z pełną listą typów, które obsługują ciągi formatu, zobacz [ciągi formatowania i typy bibliotek klas .NET](../../../standard/base-types/formatting-types.md#stringRef) w [typach formatowania w artykule .NET](../../../standard/base-types/formatting-types.md) .

Spróbuj zmodyfikować ciągi formatu w edytorze tekstów i, przy każdym wprowadzeniu zmiany, uruchom ponownie program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej. Zmień literę "d" `{date:d}` w "t" (aby wyświetlić format godziny krótkiej), "y" (w celu wyświetlenia roku i miesiąca) i "RRRR" (aby wyświetlić rok jako liczbę czterocyfrową). Zmień wartość "C2" w `{price:C2}` na "e" (dla notacji wykładniczej) i "F3" (w przypadku wartości liczbowej z trzema cyframi po przecinku dziesiętnym).

Oprócz kontrolowania formatowania można również kontrolować szerokość pola i wyrównanie sformatowanych ciągów, które są uwzględnione w ciągu wynikowym. W następnej sekcji dowiesz się, jak to zrobić.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Kontrolowanie szerokości pola i wyrównania wyrażeń interpolacji

Zwykle, gdy wynik wyrażenia interpolacji jest sformatowany do ciągu, ten ciąg jest uwzględniany w ciągu wynikowym bez spacji wiodących i końcowych. Szczególnie podczas pracy z zestawem danych, możliwość kontrolowania szerokości pola i wyrównania tekstu pomaga utworzyć bardziej czytelny wynik. Aby to zobaczyć, Zastąp cały kod w edytorze tekstu następującym kodem, a następnie wpisz `dotnet run` , aby wykonać program:

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

Nazwy autorów są wyrównane do lewej, a napisane tytuły są wyrównane do prawej strony. Wyrównanie należy określić przez dodanie przecinka (",") po wyrażeniu interpolacji i wyznaczenie *minimalnej* szerokości pola. Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównane do prawej strony. Jeśli jest to liczba ujemna, pole jest wyrównane do lewej.

Spróbuj usunąć znaki ujemne z `{"Author",-25}` kodu i `{title.Key,-25}` i ponownie uruchomić przykład, jak w poniższym kodzie:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Tym razem informacje o autorze są wyrównane do prawej strony.

Można połączyć specyfikator wyrównania i ciąg formatu dla pojedynczego wyrażenia interpolacji. W tym celu należy określić wyrównania jako pierwsze, po którym następuje dwukropek i ciąg formatu. Zamień cały kod wewnątrz `Main` metody na następujący kod, który wyświetla trzy sformatowane ciągi ze zdefiniowanymi szerokościami pól. Następnie uruchom program, wprowadzając `dotnet run` polecenie.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Dane wyjściowe wyglądają podobnie do następujących:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Samouczek interpolacji ciągów został ukończony.

Aby uzyskać więcej informacji, zobacz temat [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) i [ C# Interpolacja ciągów w](../../tutorials/string-interpolation.md) samouczku.
