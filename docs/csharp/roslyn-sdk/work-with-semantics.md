---
title: Współpracuj z modelem semantycznym zestawu .NET Compiler Platform SDK
description: Ten przegląd zawiera informacje o typie używanym do zrozumienia i manipulowania semantycznym modelem kodu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: c594447bb553f488d60fe83900e2f141608b570f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105672"
---
# <a name="work-with-semantics"></a>Korzystanie z semantyki

[Drzewa składni](work-with-syntax.md) reprezentują strukturę leksykalną i składnię kodu źródłowego. Chociaż te informacje są wystarczająco wystarczające, aby opisać wszystkie deklaracje i logikę w źródle, nie ma wystarczających informacji do zidentyfikowania elementów, do których się odwołuje. Nazwa może reprezentować:

- Typ
- pole
- Metoda
- Zmienna lokalna

Chociaż każda z nich jest unikatowa, określenie, który z nich rzeczywiście odwołuje się często, wymaga dokładnego poznania reguł języka. 

Istnieją elementy programu reprezentowane w kodzie źródłowym, a programy mogą odwoływać się również do wcześniej skompilowanych bibliotek, spakowanych w plikach zestawu. Chociaż nie ma kodu źródłowego i w związku z tym nie są dostępne żadne węzły ani drzewa składni, programy nadal mogą odwoływać się do elementów wewnątrz nich.

Dla tych zadań wymagany jest **model semantyczny**.

Oprócz modelu składni kodu źródłowego, model semantyczny hermetyzuje reguły języka, dzięki czemu można łatwo dopasować identyfikatory do poprawnego elementu programu, którego dotyczy odwołanie.

## <a name="compilation"></a>Kompilacja

Kompilacja to reprezentacja wszystkiego potrzebnego do skompilowania programu C# lub Visual Basic, który obejmuje wszystkie odwołania do zestawu, opcje kompilatora i pliki źródłowe. 

Ze względu na to, że wszystkie te informacje znajdują się w jednym miejscu, elementy zawarte w kodzie źródłowym można opisać bardziej szczegółowo. Kompilacja reprezentuje każdy zadeklarowany typ, element członkowski lub zmienną jako symbol. Kompilacja zawiera różne metody, które ułatwiają znalezienie i powiązanie symboli, które zostały zadeklarowane w kodzie źródłowym lub zaimportowane jako metadane z zestawu.

Kompilacje przypominają drzewa składniowe. Po utworzeniu kompilacji nie można jej zmienić przez Ciebie lub inną osobę, która może być udostępniana przez użytkownika. Można jednak utworzyć nową kompilację z istniejącej kompilacji, określając zmianę w taki sam sposób. Można na przykład utworzyć kompilację, która jest taka sama w każdym sposobie jak istniejąca kompilacja, z wyjątkiem, że może zawierać dodatkowy plik źródłowy lub odwołanie do zestawu.

## <a name="symbols"></a>Symbole

Symbol reprezentuje element DISTINCT zadeklarowany przez kod źródłowy lub zaimportowany z zestawu jako metadanych. Każda przestrzeń nazw, typ, metoda, właściwość, pole, zdarzenie, parametr lub zmienna lokalna jest reprezentowane przez symbol. 

Różne metody i właściwości <xref:Microsoft.CodeAnalysis.Compilation> typu pomagają znaleźć symbole. Na przykład, można znaleźć symbol dla zadeklarowanego typu według nazwy pospolitej metadanych. Możesz również uzyskać dostęp do całej tabeli symboli jako drzewa symboli, które zostały odblokowane przez globalną przestrzeń nazw.

Symbole zawierają również dodatkowe informacje, które kompilator określa ze źródła lub metadanych, takich jak inne symbole, do których istnieją odwołania. Każdy rodzaj symbolu jest reprezentowany przez oddzielny interfejs pochodny <xref:Microsoft.CodeAnalysis.ISymbol>od, każdy z własnymi metodami i właściwościami zawierającymi szczegóły informacji zebranych przez kompilator. Wiele z tych właściwości bezpośrednio odwołuje się do innych symboli. Na przykład <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> Właściwość informuje symbol rzeczywistego typu, który odwołuje się do deklaracji metody.

Symbole przedstawiają wspólną reprezentację przestrzeni nazw, typów i elementów członkowskich, między kodem źródłowym a metadanymi. Na przykład Metoda zadeklarowana w kodzie źródłowym i metoda, która została zaimportowana z metadanych, są reprezentowane przez obiekt <xref:Microsoft.CodeAnalysis.IMethodSymbol> z tymi samymi właściwościami.

Symbole są podobne do koncepcji systemu typów CLR w postaci reprezentowanej przez <xref:System.Reflection> interfejs API, ale są bogatsze w modelu, który modeluje więcej niż tylko typy. Przestrzenie nazw, zmienne lokalne i etykiety to wszystkie symbole. Ponadto symbole są reprezentacją pojęć języka, a nie pojęć środowiska CLR. Istnieje wiele nakładających się różnic, ale istnieją także liczne znaczące różnice. Na przykład Metoda iteratora w C# lub Visual Basic jest pojedynczym symbolem. Jednak gdy metoda iteratora jest tłumaczona na metadane CLR, jest to typ i wiele metod.

## <a name="semantic-model"></a>Model semantyczny

Model semantyczny reprezentuje wszystkie informacje semantyczne dla pojedynczego pliku źródłowego. Można go użyć do odnalezienia następujących danych: 

- Symbole przywoływane w określonej lokalizacji w źródle.
- Wynikowy typ dowolnego wyrażenia.
- Wszystkie diagnostyki, które są błędami i ostrzeżeniami.
- Sposób przepływu zmiennych w i poza regiony źródła.
- Odpowiedzi na bardziej spekulacyjne pytania.
