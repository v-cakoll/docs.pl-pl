---
title: Ciągi interpolowane samouczek - C# lokalnego poradniki Szybki Start
description: W tym Szybki Start o ciągi interpolowane pisania kodu C# do obejmują wynik wyrażenia w większych ciągu.
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 1edd2b9f59d1933547c4152343f226a86ad90216
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="interpolated-strings"></a>Ciągi interpolowane

Ta opcja szybkiego startu zawiera sposób użycia ciągi interpolowane w języku C# do wstawienia wartości do ciągu wyjściowego pojedynczego. Pisanie kodu C# i wyświetlić wyniki kompilowania i uruchamiania go. Procedury szybkiego startu zawiera szereg lekcje, które wstawienia wartości do ciągów i sformatować te wartości na różne sposoby.

Ta opcja szybkiego startu oczekuje, że maszynie, która służy do tworzenia aplikacji. Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux. Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego poradniki Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów. 

## <a name="create-an-interpolated-string"></a>Tworzenie ciągu interpolowanym

Utwórz katalog o nazwie **interpolowane szybkiego startu**. Stał się bieżący katalog i uruchom następujące polecenie z poziomu okna konsoli:

```console
dotnet new console -n interpolated -o .
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

Poniżej przedstawiono kilka przykładów z ciągu więcej interpolowane z innych typów danych.
    
## <a name="include-different-data-types"></a>Obejmują różne typy danych

W poprzedniej sekcji ciągu interpolowanym jest używany do wstawiania jeden ciąg wewnątrz innego. Wyrażenie ciągu interpolowanym mogą być dowolnego typu danych, mimo że. Spróbujmy ciągu interpolowanym zawierającego wartości wiele typów danych. 
    
Poniższy przykład zawiera interpolowanego wyrażenia z `Vegetable` obiektu, jest członkiem `Unit` wyliczenia, <xref:System.DateTime> wartości, a <xref:System.Decimal> wartość. Zamień wszystkie kodu C# w Edytorze następujący kod, a następnie użyj `console run` polecenie, aby uruchomić go:

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
    
Należy pamiętać, że druga interpolowane wyrażenie zawiera `item` obiektów w ciągu wynik, który jest wyświetlany w konsoli, a w tym przypadku ciągu "oberżynowego" jest umieszczona w ciągu wynik. To znaczy, ponieważ typ interpolowanego wyrażenia nie jest ciągiem, kompilator języka C# wykonuje następujące czynności:

- Jeśli jest interpolowanego wyrażenia `null`, interpolowane wyrażenie zwraca ciąg pusty ("", lub <xref:System.String.Empty?displayProperty=nameWithType>).

- Jeśli interpolowanego wyrażenia nie jest `null`, `ToString` wywoływana jest metoda typu interpolowanego wyrażenia. Można to sprawdzić przez komentowania limit definicji `Vegetable.ToString` metody w tym przykładzie, umieszczając symbol komentarza (`//`) przed nim. W danych wyjściowych, ciąg "oberżynowego" zostanie zastąpiony przez typ nazwa, "Materiałem", która jest domyślne zachowanie <xref:System.Object.ToString?displayProperty=nameWithType> metody.   

W danych wyjściowych w tym przykładzie Data jest zbyt precyzyjna (cena oberżynowego nie różnią się zależnie od drugiego), a wartość ceny nie oznacza jednostkę waluty. W następnej sekcji dowiesz się, jak rozwiązać te problemy kontrolując format ciągów zwrócony przez interpolowanego wyrażenia.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Formant formatowanie interpolowanego wyrażenia

W poprzedniej sekcji nieprawidłowo sformatowany dwa ciągi, które zostały wstawione do ciągu wynik. Jeden jest wartość daty i godziny, dla którego został właściwe tylko data. Drugi był cen, który nie poinformował jego jednostkę waluty. Problemy z obu łatwych do adresu. Interpolowanego wyrażenia mogą zawierać *ciągi formatujące* umożliwiające sterowanie formatowanie poszczególnych typów. Zmodyfikuj wywołanie `Console.WriteLine` z poprzedniego przykładu, aby uwzględnić specyfikator formatu dla pól daty i cen, jak pokazano w następującym wierszu:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
Podaj ciąg formatu, używając interpolowanego wyrażenia dwukropek i ciąg formatu. "d" jest [standardowa Data i godzina ciąg formatu](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) reprezentujący format daty krótkiej. "C2" jest [ciągu standardowego formatu liczbowego](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) reprezentujący liczbę jako wartość walutową z dwóch cyfr po punkcie dziesiętnym.

Liczba typów w bibliotek .NET Standard obsługuje zestaw wstępnie zdefiniowanych ciągi formatów. Obejmuje to wszystkie typy liczbowe oraz typy daty i godziny. Pełną listę typów, które obsługują ciągi formatów, zobacz [ciągi formatów i typy biblioteki klas .NET](../../standard/base-types/formatting-types.md#stringRef) w [typy formatowania w .NET](../../standard/base-types/formatting-types.md) artykułu. Dowolny typ może obsługiwać zestaw ciągi formatów i można również tworzyć niestandardowych rozszerzeń formatowania, które zapewniają niestandardowe formatowanie dla istniejących typów. Aby uzyskać informacje dotyczące formatowania niestandardowego, zapewniając <xref:System.ICustomFormatter> wdrażania, zobacz [niestandardowe formatowanie ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) w [typy formatowania w .NET](../../standard/base-types/formatting-types.md) artykułu.

Spróbuj zmodyfikować ciągów formatu w edytorze tekstu i, za każdym razem, wprowadzić zmiany, ponownie uruchom program, aby zobaczyć wpływ zmian na format daty i godziny oraz wartość liczbową. Zmiana "d" `{date:d}` "t" (do wyświetlania na format godziny krótkiej), "y" (Aby wyświetlić rok i miesiąc), a "yyyy" (do wyświetlania roku w postaci czterech cyfr). Zmiana "C2" `{price:C2}` "e" (w notacji wykładniczej) i "F3" (dla wartość liczbową z trzech cyfr po punkcie dziesiętnym).

Oprócz kontrolowanie formatowania, można też kontrolować pola szerokości i wyrównania ciągów zwrócony przez interpolowanego wyrażenia. W następnej sekcji dowiesz się, jak to zrobić.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Szerokość pola i wyrównanie interpolowanego wyrażenia

Zwykle gdy długość ciągu zwróconego przez wyrażenie interpolowane znajduje się w ciągu wynik, ma bez spacji wiodących lub końcowych. Szczególnie w przypadku wystąpienia, w których użytkownik pracuje z zestawu danych, interpolowanego wyrażenia pozwalają określić szerokość pola i jego wyrównania. Aby wyświetlić to Zastąp następujący kod całego kodu w edytorze tekstu, następnie wpisz `console run` do wykonania programu:
    
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
    
Nazwy autorów są wyrównane do lewej, a tytułów, które są napisane są wyrównane do lewej. Określ wyrównanie przez dodanie przecinka (",") po wyrażeniu i wyznaczające szerokości pola. Jeśli szerokość pola jest dodatnia, pole jest wyrównany do prawej:

```text
{expression, width}
```

Jeśli szerokość pola jest liczbą ujemną, pole jest wyrównane do lewej:

```text
{expression, -width}
```

Spróbuj usunąć ujemna znaki z `{"Author",-25}` i `{title.Key,-25}` interpolowane wyrażeń i ponownie uruchomić przykład, tak jak w następującym kodem:

```csharp
Console.WriteLine($"\n{"Author",25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,25}     {title.Value,30}");
```

Teraz, informacje o autorze jest wyrównany do prawej.

Szerokość pola i ciąg formatu w jednym wyrażeniu interpolowane można łączyć. Szerokość pola zostanie osiągnięty jako pierwszy, następuje dwukropek i ciąg formatu. Zamień wszystkie kodu wewnątrz `Main` metodę z następującym kodem, która zawiera trzy ciągi sformatowane z zdefiniowane szerokości pól. Następnie uruchom program wprowadzając `dotnet run` polecenia.

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
Dane wyjściowe podobne następujące czynności:

```console
1/11/2018            Hour 09                1,063.34 feet
```

Zakończono ciągi interpolowane — Szybki Start. 
    
Można kontynuować [kolekcji i tablic](arrays-and-collections.md) szybkiego startu w środowisku projektowania.

Dowiedz się więcej o ciągi interpolowane w [ciągu interpolacji](../language-reference/tokens/interpolated.md) tematu w odwołanie w C#.
