---
title: "Członkowie (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 184d4f2976b8594c308efeb113a0490499e3460e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="members-c-programming-guide"></a>Członkowie (Przewodnik programowania w języku C#)
Klasy i struktury ma elementów członkowskich, które reprezentują swoich danych i zachowania. Elementy członkowskie klasy zawierają wszystkie elementy członkowskie zadeklarowany w klasie, wraz z wszystkich elementów członkowskich (z wyjątkiem konstruktory i finalizatory) zadeklarowany w wszystkie klasy w jej hierarchii dziedziczenia. Prywatnych elementów członkowskich w klasach podstawowych są dziedziczone, ale nie są dostępne z klasy pochodnej.  
  
 W poniższej tabeli wymieniono rodzaje elementów członkowskich, które może zawierać klasy lub struktury:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)|Pola są zmiennych zadeklarowanych w zakresie klasy. Pole może być typu liczbowego wbudowanych lub wystąpienia klasy innego. Na przykład klasa kalendarza może być pola, które zawiera bieżącą datę.|  
|[Stałe](../../../csharp/programming-guide/classes-and-structs/constants.md)|Stałe są pola lub właściwości, której wartość jest ustawiana na czas kompilacji i nie można zmienić.|  
|[Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)|Właściwości są metody klasy, które są dostępne, tak jakby były pól dla tej klasy. Właściwość umożliwia ochronę pola klasy uniemożliwić zmianę bez wiedzy obiektu.|  
|[Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)|Metody zdefiniuj akcje, które można wykonywać klasy. Metody może zająć parametrów, które zawierają dane wejściowe i może zwrócić danych wyjściowych przez parametry. Metody można również zwrócić wartość bezpośrednio, bez za pomocą parametru.|  
|[Zdarzenia](../../../csharp/programming-guide/events/index.md)|Zdarzenia udostępniają powiadomienia dotyczące zdarzeń, takich jak kliknięcia przycisków lub pomyślne zakończenie metodę do innych obiektów. Zdarzenia są zdefiniowane i wyzwolone przy użyciu delegatów.|  
|[Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Przeciążone operatory są traktowane jako elementy członkowskie klasy. W przypadku przeciążenia operatora, zdefiniuj jako publicznej statycznej metody w klasie. Wstępnie zdefiniowane operatory (`+`, `*`, `<`i tak dalej) nie są traktowane jako elementy członkowskie. Aby uzyskać więcej informacji, zobacz [operatory z możliwością przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).|  
|[Indeksatory](../../../csharp/programming-guide/indexers/index.md)|Indeksatory Włącz obiektu zostać pomyślnie zindeksowane w sposób podobny do tablic.|  
|[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Konstruktory są metody, które są wywoływane po utworzeniu obiektu. Często są one używane do zainicjowania danych obiektu.|  
|[Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)|Finalizatory są bardzo rzadko używane w języku C#. Są one metod, które są wywoływane przez aparat wykonawczy środowiska, gdy obiekt jest usunięty z pamięci. Są one zazwyczaj używane do upewnij się, czy wszystkie zasoby, które muszą zostać zwolnione, są odpowiednio obsługiwane.|  
|[Zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|Zagnieżdżone typy są typami zadeklarowana wewnątrz innego typu. Zagnieżdżone typy są często używane do opisu obiektów, które są używane tylko przez typy, które je zawiera.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [Zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
 [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
 [Operatory z możliwością przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)
