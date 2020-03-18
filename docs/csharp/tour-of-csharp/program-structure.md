---
title: Struktura programu C# — zwiedzanie języka Języka C#
description: Poznaj podstawowe elementy konstrukcyjne programu C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156834"
---
# <a name="program-structure"></a>Struktura programu

Kluczowe pojęcia organizacyjne w języku C# to ***programy,*** ***przestrzenie nazw,*** ***typy,*** ***elementy członkowskie***i ***zestawy.*** Programy C# składają się z jednego lub więcej plików źródłowych. Programy deklarują typy, które zawierają elementy członkowskie i mogą być zorganizowane w przestrzenie nazw. Klasy i interfejsy są przykładami typów. Pola, metody, właściwości i zdarzenia są przykładami elementów członkowskich. Gdy programy C# są kompilowane, są fizycznie pakowane do zestawów. Zestawy zazwyczaj mają rozszerzenie `.exe` `.dll`pliku lub , w zależności od tego, czy implementują ***aplikacje*** lub ***biblioteki***, odpowiednio.

Za pomocą `dotnet new` polecenia można utworzyć projekt biblioteki o nazwie *acme:*

```console
dotnet new classlib -o acme
```

W tym projekcie deklaruj klasę o nazwie `Stack` w obszarze nazw o nazwie: `Acme.Collections`

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

W pełni kwalifikowaną nazwą `Acme.Collections.Stack`tej klasy jest . Klasa zawiera kilka elementów członkowskich: pole `top`o `Push` `Pop`nazwie , dwie metody `Entry`o nazwie i , i zagnieżdżonych klasy o nazwie . Klasa `Entry` zawiera dalej trzy elementy `next`członkowskie: pole `data`o nazwie , pole o nazwie i konstruktora. Polecenie:

```console
dotnet build
```

kompiluje przykład jako bibliotekę `Main` (kod bez punktu wejścia) `acme.dll`i tworzy zestaw o nazwie .

Zestawy zawierają kod wykonywalny w postaci instrukcji il (Intermediate Language) i symboliczne informacje w postaci metadanych. Przed jego wykonaniem kompilator Just-In-Time (JIT) programu .NET Common Language Runtime konwertuje kod IL w zestawie na kod specyficzny dla procesora.

Ponieważ zestaw jest samoopisującą się jednostką funkcji zawierającą zarówno kod, jak `#include` i metadane, nie ma potrzeby stosowania dyrektyw i plików nagłówkowych w języku C#. Typy publiczne i elementy członkowskie zawarte w określonym zestawie są udostępniane w programie C# po prostu odwołując się do tego zestawu podczas kompilowania programu. Na przykład ten program `Acme.Collections.Stack` używa `acme.dll` klasy z zestawu:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Plik *csproj* dla projektu poprzedniego programu musi zawierać węzeł odniesienia dla kompilatora C#, `acme.dll` aby rozpoznać odwołania do klas w zestawie:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Po tym `dotnet build` dodaniu tworzy zestaw `example.exe`wykonywalny o nazwie , który po uruchomieniu generuje dane wyjściowe:

```console
100
10
1
```

C# umożliwia tekst źródłowy programu mają być przechowywane w kilku plikach źródłowych. Gdy program C# z wieloma plikami jest skompilowany, wszystkie pliki źródłowe są przetwarzane razem, a pliki źródłowe mogą swobodnie odwoływać się do siebie — koncepcyjnie, to tak, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem. Deklaracje do przodu nigdy nie są potrzebne w języku C#, ponieważ z nielicznymi wyjątkami kolejność deklaracji jest nieistotna. C# nie ogranicza pliku źródłowego do deklarowania tylko jednego typu publicznego ani nie wymaga nazwy pliku źródłowego, aby dopasować typ zadeklarowany w pliku źródłowym.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](types-and-variables.md)
