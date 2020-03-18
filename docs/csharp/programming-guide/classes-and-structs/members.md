---
title: Członkowie - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: 09802431d0a5954b67687e9878f572541eeaac79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705512"
---
# <a name="members-c-programming-guide"></a>Członkowie (Przewodnik programowania w języku C#)

Klasy i struktury mają elementy członkowskie, które reprezentują ich danych i zachowania. Elementy członkowskie klasy obejmują wszystkie elementy członkowskie zadeklarowane w klasie, wraz ze wszystkimi członkami (z wyjątkiem konstruktorów i finalizatorów) zadeklarowanych we wszystkich klasach w hierarchii dziedziczenia. Prywatne elementy członkowskie w klasach podstawowych są dziedziczone, ale nie są dostępne z klas pochodnych.  
  
 W poniższej tabeli wymieniono rodzaje elementów członkowskich klasy lub struktury może zawierać:  
  
|Członek|Opis|  
|------------|-----------------|  
|[Pola](./fields.md)|Pola są zmiennymi zadeklarowanymi w zakresie klasy. Pole może być wbudowanym typem liczbowym lub wystąpieniem innej klasy. Na przykład klasa kalendarza może mieć pole zawierające bieżącą datę.|  
|[Stałe](./constants.md)|Stałe są pola, których wartość jest ustawiona w czasie kompilacji i nie można zmienić.|  
|[Właściwości](./properties.md)|Właściwości są metody w klasie, które są dostępne tak, jakby były pola w tej klasie. Właściwość może zapewnić ochronę pola klasy, aby zaradzić jego przed zmianą bez znajomości obiektu.|  
|[Metody](./methods.md)|Metody definiują akcje, które może wykonać klasa. Metody mogą przyjmować parametry, które dostarczają danych wejściowych i mogą zwracać dane wyjściowe za pomocą parametrów. Metody mogą również zwracać wartość bezpośrednio, bez użycia parametru.|  
|[Zdarzenia](../events/index.md)|Zdarzenia zawierają powiadomienia o wystąpieniach, takie jak kliknięcia przycisków lub pomyślne ukończenie metody, do innych obiektów. Zdarzenia są definiowane i wyzwalane przy użyciu delegatów.|  
|[Operatory](../../language-reference/operators/index.md)|Przeciążone operatory są uważane za elementy członkowskie typu. Podczas przeciążenia operatora, można zdefiniować go jako publiczną metodę statyczną w typie. Aby uzyskać więcej informacji, zobacz [Przeciążenie operatora](../../language-reference/operators/operator-overloading.md).|  
|[Indexers](../indexers/index.md) (Indeksatory)|Indeksatory umożliwiają indeksowanie obiektu w sposób podobny do tablic.|  
|[Konstruktory](./constructors.md)|Konstruktory są metody, które są wywoływane podczas tworzenia obiektu po raz pierwszy. Są one często używane do inicjowania danych obiektu.|  
|[Finalizatory](./destructors.md)|Finalizatory są używane bardzo rzadko w języku C#. Są to metody, które są wywoływane przez aparat wykonywania wykonawczego, gdy obiekt ma zostać usunięty z pamięci. Są one zazwyczaj używane, aby upewnić się, że wszystkie zasoby, które muszą być zwolnione są obsługiwane odpowiednio.|  
|[Zagnieżdżone typy](./nested-types.md)|Typy zagnieżdżone są typami zadeklarowanych w ramach innego typu. Typy zagnieżdżone są często używane do opisywania obiektów, które są używane tylko przez typy, które je zawierają.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy](./classes.md)
