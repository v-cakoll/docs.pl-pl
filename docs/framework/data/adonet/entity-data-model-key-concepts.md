---
title: Kluczowe założenia modelu danych jednostki
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: 5e4fc0c960d7dac289852df3b080c7e49d1d1c10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795563"
---
# <a name="entity-data-model-key-concepts"></a>Kluczowe założenia modelu danych jednostki
Entity Data Model (EDM) używa trzech najważniejszych koncepcji do opisywania struktury danych: *typu jednostki*, *typu skojarzenia*i *Właściwości*. Są to najważniejsze pojęcia dotyczące opisywania struktury danych w dowolnej implementacji modelu EDM.  
  
## <a name="entity-type"></a>Typ jednostki  
 [Typ jednostki](entity-type.md) jest podstawowym blokiem konstrukcyjnym opisującym strukturę danych z Entity Data Model. W modelu koncepcyjnym typy jednostek są zbudowane z [Właściwości](property.md) i opisują strukturę koncepcji najwyższego poziomu, takich jak klienci i zamówienia w aplikacji biznesowej. W taki sam sposób, w jaki definicja klasy w programie komputerowym jest szablonem wystąpień klasy, typ jednostki jest szablon dla jednostek. Jednostka reprezentuje konkretny obiekt (na przykład konkretny klient lub zamówienie). Każda jednostka musi mieć unikatowy [klucz jednostki](entity-key.md) w ramach [zestawu jednostek](entity-set.md).  Zestaw jednostek jest kolekcją wystąpień określonego typu jednostki. Zestawy jednostek (i [zestawy skojarzeń](association-set.md)) są logicznie pogrupowane w [kontenerze jednostek](entity-container.md).  
  
 Dziedziczenie jest obsługiwane w przypadku typów jednostek: to oznacza, że jeden typ jednostki może pochodzić od innego. Aby uzyskać więcej informacji, [zobacz Entity Data Model: Dziedziczenie](entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>Typ skojarzenia  
 [Typ skojarzenia](association-type.md) (nazywany także skojarzeniem) to podstawowy blok konstrukcyjny do opisywania relacji w Entity Data Model. W modelu koncepcyjnym skojarzenie reprezentuje relację między dwoma typami jednostek (np. klientem i kolejnością). Każde skojarzenie ma dwa [punkty końcowe skojarzenia](association-end.md) , które określają typy jednostek objęte skojarzeniem. Każdy punkt końcowy skojarzenia określa również [liczebność końcową skojarzenia](association-end-multiplicity.md) , która wskazuje liczbę jednostek, które mogą znajdować się na tym końcu skojarzenia. Liczebność końcowa skojarzenia może mieć wartość jednego (1), zero lub jeden (0.. 1) lub wiele (\*). Do jednostek na jednym końcu skojarzenia można uzyskać dostęp za poorednictwem [właściwości nawigacji](navigation-property.md)lub kluczy obcych, jeśli są one uwidocznione w typie jednostki. Aby uzyskać więcej informacji, zobacz [Właściwość klucza obcego](foreign-key-property.md).  
  
 W aplikacji wystąpienie skojarzenia reprezentuje określone skojarzenie (takie jak skojarzenie między wystąpieniem klienta i wystąpieniami zamówienia). Wystąpienia skojarzeń są logicznie pogrupowane w [zestawie skojarzenia](association-set.md). Zestawy skojarzeń (i [zestawy jednostek](entity-set.md)) są logicznie pogrupowane w [kontenerze jednostek](entity-container.md).  
  
## <a name="property"></a>Właściwość  
 [Typy jednostek](entity-type.md) zawierają [Właściwości](property.md) definiujące ich strukturę i cechy. Na przykład typ jednostki klienta może mieć właściwości, takie jak CustomerId, Name i Address.  
  
 Właściwości w modelu koncepcyjnym są analogiczne do właściwości zdefiniowanych w klasie w programie komputerowym. W taki sam sposób, w jaki właściwości klasy definiują kształt klasy i zawierają informacje o obiektach, właściwości w modelu koncepcyjnym definiują kształt typu jednostki i zawierają informacje o wystąpieniach typu jednostki.  
  
 Właściwość może zawierać dane pierwotne (takie jak ciąg, liczba całkowita lub wartość logiczna) lub dane strukturalne (takie jak typ złożony). Aby uzyskać więcej informacji, [zobacz Entity Data Model: Typy](entity-data-model-primitive-data-types.md)danych pierwotnych.  
  
## <a name="representations-of-a-conceptual-model"></a>Reprezentacje modelu koncepcyjnego  
 *Model koncepcyjny* jest określoną reprezentacją struktury niektórych danych jako jednostek i relacji. Jednym ze sposobów reprezentowania modelu koncepcyjnego jest diagram. Poniższy diagram przedstawia model koncepcyjny z trzema typami jednostek (`Book`, `Publisher`i `Author`) oraz dwoma skojarzeniami (`PublishedBy` i `WrittenBy`):  
  
 ![Diagram przedstawiający model koncepcyjny z trzema typami jednostek.](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 Jednakże ta reprezentacja ma pewne niedociągnięcia, gdy chodzi o przekazywanie pewnych szczegółów dotyczących modelu. Na przykład typ właściwości i informacje o zestawie jednostek nie są przekazywane na diagramie. Przejrzystość modelu koncepcyjnego może być przekazana dokładniej przy użyciu języka specyficznego dla domeny (DSL). [ADO.NET Entity Framework](./ef/index.md) korzysta z opartego na języku XML języka DSL zwanego *językiem definicji schematu koncepcyjnego* ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniżej znajduje się definicja CSDL modelu koncepcyjnego na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Zobacz także

- [Model danych jednostki](entity-data-model.md)
