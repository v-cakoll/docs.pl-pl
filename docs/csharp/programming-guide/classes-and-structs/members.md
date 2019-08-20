---
title: Członkowie — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: 64df7d6be09ae670307fa1cf1d66dfdf8e78a7a6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596416"
---
# <a name="members-c-programming-guide"></a>Członkowie (Przewodnik programowania w języku C#)

Klasy i struktury mają składowe reprezentujące ich dane i zachowanie. Elementy członkowskie klasy obejmują wszystkie elementy członkowskie zadeklarowane w klasie oraz wszystkie elementy członkowskie (z wyjątkiem konstruktorów i finalizatorów) zadeklarowane we wszystkich klasach w hierarchii dziedziczenia. Prywatne składowe w klasach bazowych są dziedziczone, ale nie są dostępne z klas pochodnych.  
  
 Poniższa tabela zawiera listę rodzajów elementów członkowskich, które może zawierać Klasa lub struktura:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Pola](./fields.md)|Pola są zmiennymi zadeklarowanymi w zakresie klasy. Pole może być wbudowanym typem liczbowym lub wystąpieniem innej klasy. Na przykład Klasa kalendarza może mieć pole zawierające bieżącą datę.|  
|[Stałe](./constants.md)|Stałe są polami, których wartość jest ustawiona w czasie kompilacji i nie można jej zmienić.|  
|[Właściwości](./properties.md)|Właściwości są metodami klasy, które są dostępne, tak jakby były polami w tej klasie. Właściwość może zapewnić ochronę pola klasy, aby zachować jego zmianę bez znajomości obiektu.|  
|[Metody](./methods.md)|Metody definiują akcje, które może wykonać Klasa. Metody mogą przyjmować parametry, które zapewniają dane wejściowe i mogą zwracać dane wyjściowe za poorednictwem parametrów. Metody mogą również zwracać wartość bezpośrednio, bez użycia parametru.|  
|[Zdarzenia](../events/index.md)|Zdarzenia udostępniają powiadomienia o wystąpieniach, takie jak kliknięcia przycisków lub pomyślne zakończenie metody, do innych obiektów. Zdarzenia są definiowane i wyzwalane za pomocą delegatów.|  
|[Operatory](../statements-expressions-operators/operators.md)|Przeciążone operatory są uznawane za składowe typu. Po przeciążeniu operatora należy go zdefiniować jako publiczną metodę statyczną w typie. Aby uzyskać więcej informacji, zobacz przeciążanie [operatora](../../language-reference/operators/operator-overloading.md).|  
|[Indeksatory](../indexers/index.md)|Indeksatory umożliwiają indeksowanie obiektów w sposób podobny do tablic.|  
|[Konstruktory](./constructors.md)|Konstruktory to metody, które są wywoływane, gdy obiekt jest tworzony po raz pierwszy. Są one często używane do inicjowania danych obiektu.|  
|[Finalizatory](./destructors.md)|Finalizatory są używane bardzo rzadko w C#programie. Są to metody, które są wywoływane przez aparat wykonywania środowiska uruchomieniowego, gdy obiekt zostanie usunięty z pamięci. Są one zwykle używane do upewnienia się, że wszystkie zasoby, które muszą zostać wydane, są odpowiednio obsługiwane.|  
|[Zagnieżdżone typy](./nested-types.md)|Typy zagnieżdżone są typami zadeklarowanymi w innym typie. Typy zagnieżdżone są często używane do opisywania obiektów, które są używane tylko przez typy, które je zawierają.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy](./classes.md)
- [Metody](./methods.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
- [Właściwości](./properties.md)
- [Pola](./fields.md)
- [Indeksatory](../indexers/index.md)
- [Zdarzenia](../events/index.md)
- [Zagnieżdżone typy](./nested-types.md)
- [Operatory](../statements-expressions-operators/operators.md)
