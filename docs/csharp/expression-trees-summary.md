---
title: Podsumowanie drzew wyrażeń
description: Recaps, jak używanie drzew wyrażeń do tworzenia dynamicznych programów, które interpretacji kodu jako danych i tworzenie nowych funkcji, na podstawie tego kodu.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: e0d46aa67b61fd4e1d2bcc20b4a567524bb00301
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees-summary"></a>Podsumowanie drzew wyrażeń

[Poprzednie — Tłumaczenia wyrażenia](expression-trees-translating.md)

W tej serii przedstawiono sposób korzystania *drzew wyrażeń* do tworzenia dynamicznych programów, które interpretacji kodu jako danych i tworzenie nowych funkcji, na podstawie tego kodu.

Można sprawdzić drzew wyrażeń do zrozumienia celem algorytmu. Nie można tylko badanie tego kodu. Można utworzyć nowego drzew wyrażeń, które reprezentują zmodyfikowanej wersji oryginalnego kodu.

Można również używanie drzew wyrażeń do przyjrzeć się algorytm i tłumaczenie tego algorytmu inny język lub środowiska. 

## <a name="limitations"></a>Ograniczenia

Istnieją pewne nowszej C# języka elementy, które nie je łatwo przekształcić w drzewach wyrażeń. Drzewa wyrażeń nie może zawierać `await` wyrażenia, lub `async` wyrażenia lambda. Funkcje dodane w wersji języka C# 6 nie pojawiają się dokładnie, jak podano w drzewach wyrażeń. Zamiast tego nowsze funkcje mają być widoczne w drzewach wyrażeń w składni równorzędną, wcześniej. To nie może być jako część ograniczenia jak się wydaje. W rzeczywistości oznacza to, że swój kod, który interpretuje drzew wyrażeń będzie prawdopodobnie nadal działać w identyczny gdy wprowadzono nowe funkcje języka.

Nawet w przypadku tych ograniczeń drzew wyrażeń umożliwiają tworzenie dynamicznych algorytmy, które opierają się na interpretowanie i modyfikowania kodu, który jest reprezentowany jako struktury danych. Jest zaawansowanym narzędziem i jest jedną z funkcji ekosystemu .NET, który umożliwia sformatowanego biblioteki, takich jak Entity Framework w celu ich działania.

