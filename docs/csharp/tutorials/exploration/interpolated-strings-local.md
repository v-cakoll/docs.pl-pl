---
title: Interpolacja - ciągów C# samouczek
description: W tym samouczku dowiesz się, jak używać C# funkcji interpolacji ciągów, aby uwzględnić wyrażenie sformatowane wyniki w dłuższym ciągu.
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: c1e6fed2293b7447384a657e720fb847f2fa041f
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195895"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Konstruowania sformatowane ciągi za pomocą Interpolacja ciągów

W tym samouczku pokazano sposób użycia C# [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) wstawiania wartości do ciągu pojedynczego wyniku. Możesz pisać kod w języku C# i zobaczyć wyniki kompilowania i uruchamiania ich. Samouczek zawiera serię lekcji, które przedstawiają sposób wstawiania wartości do ciągów i formatują te wartości na różne sposoby.

W tym samouczku oczekuje, że masz maszyny, których można użyć do tworzenia aplikacji. Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux. Można też wykonać [interaktywne wersji](interpolated-strings.yml) po ukończeniu tego samouczka w przeglądarce.

## <a name="create-an-interpolated-string"></a>Tworzenie ciągu interpolowanego

Utwórz katalog o nazwie **interpolowane**. Przekształcić ją w bieżącym katalogu i uruchom następujące polecenie z okna konsoli:

```console
dotnet new console
```

To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.

Otwórz **Program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem, gdzie możesz zastąpić `<name>` z Twoją nazwą:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli. Kiedy uruchamiasz program, wyświetla pojedynczy ciąg, z Twoim imieniem w powitaniu. Ciąg umieszczony w <xref:System.Console.WriteLine%2A> jest wywołanie metody *interpolowane wyrażenia ciągu*. Jest to rodzaj szablonu, który umożliwia skonstruowanie pojedynczego ciągu (o nazwie *ciągiem wynikowym*) z ciągu obejmującego osadzony kod. Ciągi interpolowane są szczególnie użyteczne do wstawiania wartości do ciągu lub łączenia (łączenie) ciągów.

Ten prosty przykład zawiera dwa elementy, które muszą mieć każdy ciąg interpolowany:

- Literał ciągu rozpoczynający się od `$` znak przed jego otwierającym znakiem cudzysłowu. Nie może być spacji między `$` symboli i znaku cudzysłowu. (Jeśli chcesz zobaczyć, co się stanie po wstawieniu odstępu, Wstaw go po `$` znak, Zapisz plik i ponownie uruchom program, wpisując `dotnet run` w oknie konsoli. C# Kompilator wyświetla komunikat o błędzie "Błąd CS1056: Nieoczekiwany znak '$' ".)

- Co najmniej jeden *wyrażeń interpolacji*. Wyrażenie interpolacji jest wskazywane przez nawias klamrowy otwierający i zamykający (`{` i `}`). Możesz umieścić dowolne C# wyrażenie zwracające wartość (w tym `null`) wewnątrz nawiasów klamrowych.

Wypróbujmy kilka dodatkowych przykładowych interpolacji ciągu z innymi typami danych.

## <a name="include-different-data-types"></a>Uwzględnianie innych typów danych

W poprzedniej sekcji Interpolacja ciągów jest używany do wstawienia jednego ciągu wewnątrz innego. Wynik wyrażenia interpolacji może być dowolnego typu danych, mimo że. Teraz zawierać wartości różnych typów danych w ciągu interpolowanym.

W poniższym przykładzie, najpierw należy zdefiniować [klasy](../../programming-guide/classes-and-structs/classes.md) — typ danych `Vegetable` zawierający `Name` [właściwość](../../properties.md) i `ToString` [metoda](../../methods.md), które [zastępuje](../../language-reference/keywords/override.md) zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody. [ `public` Modyfikator dostępu](../../language-reference/keywords/public.md) sprawia, że tej metody jest dostępny dla dowolnego kodu klienta, można pobrać reprezentacji w postaci ciągu `Vegetable` wystąpienia. W przykładzie `Vegetable.ToString` metoda zwraca wartość `Name` właściwości, który jest inicjowany w `Vegetable` [Konstruktor](../../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Następnie tworzymy wystąpienie `Vegetable` klasę o nazwie `item` przy użyciu [ `new` — słowo kluczowe](../../language-reference/keywords/new-operator.md) i podanie nazwy dla konstruktora `Vegetable`:

```csharp
var item = new Vegetable("eggplant");
```

Na koniec dołączamy `item` zmiennej do ciągu interpolowanego, który zawiera także <xref:System.DateTime> wartość <xref:System.Decimal> wartości i `Unit` [wyliczenie](../../programming-guide/enumeration-types.md) wartość. Zastąp cały kod C# w edytorze następującym kodem, a następnie użyj `dotnet run` polecenie, aby go uruchomić:

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

Należy pamiętać, że wyrażenie interpolacji `item` w ciągu interpolowanym jest rozpoznawany jako tekst "eggplant" w ciągu wynikowym. To dlatego, gdy typ wyniku wyrażenia nie jest ciągiem, wynik jest tłumaczona na ciąg w następujący sposób:

- Jeśli wyrażenie interpolacji ma `null`, ciąg pusty ("", lub <xref:System.String.Empty?displayProperty=nameWithType>) jest używany.

- Jeśli wyrażenia interpolacji nie być `null`, zazwyczaj `ToString` zostanie wywołana metoda typ wyniku. Można to sprawdzić, aktualizując wykonania `Vegetable.ToString` metody. Może nawet trzeba zaimplementować `ToString` metody, ponieważ każdy typ ma pewne implementacja tej metody. Aby to przetestować, przekształcić w komentarz definicję `Vegetable.ToString` metody w przykładzie (w tym celu należy umieścić symbol komentarza `//`, przed nim). W danych wyjściowych ciąg "eggplant" został zastąpiony w pełni kwalifikowana nazwa typu ("roślinnego" w tym przykładzie), który jest domyślnym zachowaniem z <xref:System.Object.ToString?displayProperty=nameWithType> metody. Domyślne zachowanie `ToString` metodą wartość wyliczenia jest zwraca reprezentację ciągu wartości.

W danych wyjściowych z tego przykładu Data jest zbyt precyzyjna (cena eggplant nie zmienia się każda sekunda), a wartość ceny nie wskazuje jednostkę waluty. W następnej sekcji dowiesz się, jak rozwiązać te problemy, kontrolując format ciągów reprezentujących wyniki wyrażenia.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Kontrolowanie formatowania wyrażeń interpolacji

W poprzedniej sekcji dwa nie najlepiej sformatowane ciągi zostały wstawione do ciągu wynikowego. Jedna była wartość daty i godziny, dla którego tylko data powinna mieć zastosowanie. Drugim była cena, która nie wskazywała waluty. Zarówno w przypadku problemów są łatwe do adresu. Interpolacja ciągów pozwala określić *ciągi formatujące* które kontrolują formatowanie poszczególnych typów. Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby dołączyć ciągi formatu daty i ceny wyrażeń, jak pokazano w następującym wierszu:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Należy określić ciąg formatu wykonując wyrażenie interpolacji z dwukropkiem (":") i ciąg formatu. "d" jest [ciąg formatu standardowego daty i godziny](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) reprezentujący formatu daty krótkiej. "C2" to [standardowy Ciąg formatujący](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) reprezentujący liczbę jako wartość waluty z dwoma cyframi po separatorze dziesiętnym.

Liczba typów w bibliotekach .NET obsługuje wstępnie zdefiniowany zestaw ciągów formatu. Dotyczy to wszystkich typów liczbowych i typów daty i godziny. Aby uzyskać pełną listę typów, które obsługują ciągi formatu, zobacz [ciągi formatu i typy biblioteki klas .NET](../../../standard/base-types/formatting-types.md#stringRef) w [typy formatowania na platformie .NET](../../../standard/base-types/formatting-types.md) artykułu.

Spróbuj zmodyfikować ciągi formatu w edytorze tekstu i, za każdym razem, wprowadzić zmiany, ponownie uruchom program, aby zobaczyć, jak zmiany wpływają na formatowanie daty i godziny oraz wartości liczbowej. Zmień "d" w `{date:d}` na "t" (Aby wyświetlić krótki format daty), "y" (Aby wyświetlić rok i miesiąc) oraz "yyyy" (Aby wyświetlać rok jako liczbę czterocyfrową). Zmień "C2" w `{price:C2}` "e" (notacja wykładnicza) oraz "F3" (wartość liczbową z trzema cyframi po separatorze dziesiętnym).

Poza kontrolowaniem formatowania możesz też kontrolować szerokość pola i wyrównanie sformatowanego ciągów, które znajdują się w ciągu wynikowym. W następnej sekcji dowiesz się, jak to zrobić.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Kontrolowanie szerokości pola i wyrównania wyrażeń interpolacji

Zazwyczaj gdy wynikiem wyrażenia interpolacji jest sformatowany ciąg, ciąg znajduje się w ciągu wynikowym bez spacji wiodących albo końcowych. Szczególnie podczas pracy z zestawem danych, można kontrolować szerokość pola i wyrównanie tekstu pozwala tworzyć bardziej czytelny dane wyjściowe. Aby to zobaczyć, Zastąp cały kod w edytorze tekstu z następującym kodem, a następnie wpisz `dotnet run` do wykonania programu:

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

Nazwy autorzy są wyrównane do lewej, a tytułów, które one napisane są wyrównane do prawej. Wyrównanie określa się poprzez dodanie przecinka (",") po interpolacji wyrażeniu i określenie *minimalne* szerokości pola. Jeśli określona wartość jest liczbą dodatnią, pole jest wyrównany do prawej. Jeśli jest liczbą ujemną, pole jest wyrównany do lewej.

Spróbuj usunąć znaki ujemne z `{"Author",-25}` i `{title.Key,-25}` kodu i uruchomić przykładowy kod ponownie, tak jak w poniższym kodzie:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Ten czas, informacje o autorze jest wyrównany do prawej.

Możesz połączyć specyfikator wyrównania i ciąg formatu interpolacji pojedynczego wyrażenia. Aby to zrobić, określ wyrównanie najpierw następuje dwukropek i ciąg formatu. Zastąp cały kod wewnątrz `Main` metoda następującym kodem, który wyświetla trzy sformatowane ciągi ze zdefiniowanych szerokościami pól. Następnie uruchom program, wprowadzając `dotnet run` polecenia.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

Dane wyjściowe wyglądają następująco:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Pomyślnie ukończono samouczek interpolacji ciągu.

Aby uzyskać więcej informacji, zobacz [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) tematu i [Interpolacja w języku C# ciągów](../../tutorials/string-interpolation.md) samouczka.
