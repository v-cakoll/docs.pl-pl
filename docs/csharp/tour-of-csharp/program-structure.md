---
title: Struktura programu w języku c# — Przewodnik po języku C#
description: Zapoznaj się z podstawowymi blokami konstrukcyjnymi programu C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c0a4dcaed7b53a7da7008d6000b3bec2ffe3ee7b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141012"
---
# <a name="program-structure"></a>Struktura programu

Kluczowe koncepcje organizacyjne w języku C# to ***programy***, ***przestrzenie nazw***, ***typy***, ***elementy członkowskie***i ***zestawy***. Programy w języku C# składają się z co najmniej jednego pliku źródłowego. Programy deklarują typy, które zawierają składowe i mogą być zorganizowane w przestrzenie nazw. Klasy i interfejsy są przykładami typów. Pola, metody, właściwości i zdarzenia są przykładami elementów członkowskich. Po skompilowaniu programów C# są one fizycznie spakowane w zestawy. Zestawy zazwyczaj `.exe` mają rozszerzenie pliku lub `.dll`, w zależności od tego, czy implementują odpowiednio ***aplikacje*** lub ***biblioteki***.

Można utworzyć projekt biblioteki o nazwie *Acme* przy użyciu `dotnet new` polecenia:

```dotnetcli
dotnet new classlib -o acme
```

W tym projekcie Zadeklaruj klasę o nazwie `Stack` w przestrzeni nazw o `Acme.Collections`nazwie:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

W pełni kwalifikowana nazwa tej klasy to `Acme.Collections.Stack`. Klasa zawiera kilka elementów członkowskich: pole o nazwie `top`, dwie metody o `Push` nazwie `Pop`i i zagnieżdżoną klasę o `Entry`nazwie. `Entry` Klasa dodatkowo zawiera trzy elementy członkowskie: pole o nazwie `next`, pole o nazwie `data`i Konstruktor. Polecenie:

```dotnetcli
dotnet build
```

kompiluje przykład jako bibliotekę (kod bez punktu `Main` wejścia) i tworzy zestaw o nazwie. `acme.dll`

Zestawy zawierają kod wykonywalny w postaci instrukcji języka pośredniego (IL) i informacji symbolicznych w formie metadanych. Przed wykonaniem, kompilator just-in-Time (JIT) środowiska uruchomieniowego języka wspólnego .NET konwertuje kod IL w zestawie na kod specyficzny dla procesora.

Ponieważ zestaw jest samoopisującą się jednostką funkcji obejmujących zarówno kod, jak i metadane, nie ma potrzeby `#include` stosowania dyrektyw i plików nagłówkowych w języku C#. Typy publiczne i składowe zawarte w określonym zestawie są udostępniane w programie C# po prostu przez odwołanie się do tego zestawu podczas kompilowania programu. Na przykład ten program używa `Acme.Collections.Stack` klasy z `acme.dll` zestawu:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Plik *csproj* dla projektu poprzedniego programu musi zawierać węzeł odniesienia dla kompilatora C# w celu rozpoznania odwołań do klas w `acme.dll` zestawie:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Po tym dodaniu `dotnet build` program tworzy zestaw wykonywalny `example.exe`o nazwie, który po uruchomieniu generuje dane wyjściowe:

```dotnetcli
100
10
1
```

Język C# umożliwia przechowywanie tekstu źródłowego programu w kilku plikach źródłowych. Podczas kompilowania wieloplikowego programu w języku C# wszystkie pliki źródłowe są przetwarzane razem, a pliki źródłowe mogą swobodnie odwoływać się do siebie nawzajem — jest to tak samo, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem. Deklaracje przesyłania dalej nie są nigdy konieczne w języku C#, ponieważ z kilkoma wyjątkami porządek deklaracji jest nieważny. Język C# nie ogranicza pliku źródłowego do deklarowania tylko jednego typu publicznego ani nie wymaga, aby nazwa pliku źródłowego była zgodna z typem zadeklarowanym w pliku źródłowym.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](types-and-variables.md)
