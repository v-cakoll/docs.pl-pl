---
title: C#Struktura programu — Przewodnik po C# języku
description: Zapoznaj się z podstawowymi blokami konstrukcyjnymi C# programu
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 828146ba509daf9427e6dd1a4ebf3ad747ac7c39
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159120"
---
# <a name="program-structure"></a>Struktura programu

Kluczowe koncepcje organizacyjne C# w programie to ***programy***, ***przestrzenie nazw***, ***typy***, ***elementy członkowskie***i ***zestawy***. C#programy składają się z co najmniej jednego pliku źródłowego. Programy deklarują typy, które zawierają składowe i mogą być zorganizowane w przestrzenie nazw. Klasy i interfejsy są przykładami typów. Pola, metody, właściwości i zdarzenia są przykładami elementów członkowskich. Gdy C# programy są kompilowane, są fizycznie spakowane w zestawy. Zestawy zazwyczaj mają rozszerzenie pliku `.exe` lub `.dll`, w zależności od tego, czy implementują odpowiednio ***aplikacje*** lub ***biblioteki***.

Można utworzyć projekt biblioteki o nazwie *Acme* przy użyciu polecenia `dotnet new`:

```console
dotnet new classlib -o acme
```

W tym projekcie Zadeklaruj klasę o nazwie `Stack` w przestrzeni nazw o nazwie `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

W pełni kwalifikowana nazwa tej klasy jest `Acme.Collections.Stack`. Klasa zawiera kilka elementów członkowskich: pole o nazwie `top`, dwie metody o nazwie `Push` i `Pop`oraz zagnieżdżoną klasę o nazwie `Entry`. Klasa `Entry` dodatkowo zawiera trzy elementy członkowskie: pole o nazwie `next`, pole o nazwie `data`i Konstruktor. Polecenie:

```console
dotnet build 
```

kompiluje przykład jako bibliotekę (kod bez punktu wejścia `Main`) i tworzy zestaw o nazwie `acme.dll`.

Zestawy zawierają kod wykonywalny w postaci instrukcji języka pośredniego (IL) i informacji symbolicznych w formie metadanych. Przed wykonaniem, kompilator just-in-Time (JIT) środowiska uruchomieniowego języka wspólnego .NET konwertuje kod IL w zestawie na kod specyficzny dla procesora.

Ponieważ zestaw jest samoopisującą się jednostką funkcji obejmujących zarówno kod, jak i metadane, nie ma potrzeby stosowania dyrektyw `#include` i plików nagłówkowych w programie C#. Typy publiczne i składowe zawarte w określonym zestawie są udostępniane w C# programie po prostu przez odwołanie się do tego zestawu podczas kompilowania programu. Na przykład ten program używa klasy `Acme.Collections.Stack` z zestawu `acme.dll`:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Plik *csproj* dla projektu poprzedniego programu musi zawierać węzeł odniesienia dla kompilatora, C# aby rozpoznać odwołania do klas w zestawie `acme.dll`:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Po tym dodaniu `dotnet build` tworzy zestaw wykonywalny o nazwie `example.exe`, który w przypadku uruchamiania generuje dane wyjściowe:

```console
100
10
1
```

C#zezwala na przechowywanie tekstu źródłowego programu w kilku plikach źródłowych. W przypadku kompilowania programu C# z obsługą wielu plików wszystkie pliki źródłowe są przetwarzane razem, a pliki źródłowe mogą swobodnie odwoływać się do siebie nawzajem — jest to tak samo, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem. Deklaracje przesyłania dalej nie są C# nigdy niewymagane w programie, dlatego z kilkoma wyjątkami porządek deklaracji jest nieważny. C#nie ogranicza pliku źródłowego do deklarowania tylko jednego typu publicznego ani nie wymaga, aby nazwa pliku źródłowego była zgodna z typem zadeklarowanym w pliku źródłowym.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](types-and-variables.md)
