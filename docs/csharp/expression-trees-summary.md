---
title: Podsumowanie drzew wyrażeń
description: Podsumowania, jak można użyć drzew wyrażeń do tworzenia dynamicznych programów, które interpretacji kodu jako dane oraz tworzyć nowe funkcje, w oparciu o ten kod.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 99b9463df096d3aada19ed7995b04ef4bd41c179
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148632"
---
# <a name="expression-trees-summary"></a>Podsumowanie drzew wyrażeń

[Poprzednie — Translacja wyrażeń](expression-trees-translating.md)

W tej serii przedstawiono sposób korzystania *drzew wyrażeń* do tworzenia dynamicznych programów, które interpretacji kodu jako dane oraz tworzyć nowe funkcje, w oparciu o ten kod.

Można sprawdzić w drzewach wyrażeń w celu zrozumienia intencji algorytmu. Ten kod nie może tylko sprawdzić. Można tworzyć nowe drzew wyrażeń, które reprezentują zmodyfikowanej wersji oryginalnego kodu.

Można również używanie drzew wyrażeń do wzięcia pod algorytmu i tłumaczenie tego algorytmu innego języka lub środowiska. 

## <a name="limitations"></a>Ograniczenia

Brak niektórych nowszych C# elementów języka, które nie je łatwo przekształcić w drzewach wyrażeń. Drzewa wyrażeń nie może zawierać `await` wyrażeń, lub `async` wyrażenia lambda. Funkcje dodane w wielu C# wersji 6 nie pojawiają się dokładnie tak jak napisane w drzewach wyrażeń. Zamiast tego nowsze funkcje zostaną ujawnione w drzewach wyrażeń w składni jego odpowiednika, wcześniej. To może nie być tyle to ograniczenie może myśląc. W rzeczywistości oznacza to, że swój kod, który interpretuje drzew wyrażeń będzie prawdopodobnie nadal działać tak samo, gdy zostaną wprowadzone nowe funkcje języka.

Nawet w przypadku tych ograniczeń drzew wyrażeń umożliwiają tworzenie dynamicznych algorytmy, które opierają się na interpretowaniu i modyfikowania kodu, który jest reprezentowany jako struktury danych. Jest zaawansowanym narzędziem, i jest jedną z funkcji ekosystemu .NET, która umożliwia zaawansowane biblioteki, takim jak Entity Framework, aby osiągnąć, co robią.
