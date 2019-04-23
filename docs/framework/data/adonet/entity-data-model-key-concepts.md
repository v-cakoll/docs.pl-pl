---
title: Kluczowe założenia modelu danych jednostki
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: 2efa54b6bd656129812cc9dd7c2ce38a4fb2a89a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074459"
---
# <a name="entity-data-model-key-concepts"></a>Kluczowe założenia modelu danych jednostki
Do opisania struktury danych Entity Data Model (EDM) używa trzech kluczowych pojęć: *typu jednostki*, *typ skojarzenia*, i *właściwość*. Oto najważniejsze pojęcia do opisywania struktury danych w implementacji EDM.  
  
## <a name="entity-type"></a>Typ jednostki  
 [Typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) jest elementem składowym podstawowych do opisywania struktury danych z modelu Entity Data Model. W modelu koncepcyjnym, typy jednostek są konstruowane na podstawie [właściwości](../../../../docs/framework/data/adonet/property.md) i opisz strukturę koncepcje najwyższego poziomu, takich jak klienci i zamówienia w aplikacji biznesowej. W ten sam sposób czy definicję klasy w program komputerowy jest szablonem dla wystąpienia klasy, typ jednostki jest szablonem dla jednostki. Jednostka reprezentuje określonego obiektu (na przykład konkretnego klienta lub zamówienia). Każda jednostka musi mieć unikatową [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) w ramach [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md).  Zestaw jednostek jest kolekcją wystąpień określonego typu. Zestawy jednostek (i [zestawów skojarzeń](../../../../docs/framework/data/adonet/association-set.md)) są logicznie pogrupowane w [kontener jednostek](../../../../docs/framework/data/adonet/entity-container.md).  
  
 Dziedziczenie jest obsługiwana przy użyciu typów jednostek: oznacza to, co typ jednostki może pochodzić z innej. Aby uzyskać więcej informacji, zobacz [modelu danych jednostki: Dziedziczenie](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>Typ skojarzenia  
 [Typ skojarzenia](../../../../docs/framework/data/adonet/association-type.md) (nazywane również skojarzenie) jest elementem składowym podstawowych do opisywania relacji w modelu Entity Data Model. W modelu koncepcyjnym skojarzenia reprezentuje relację między dwoma typami encji (na przykład klienta i zamówienia). Każde skojarzenie ma dwa [skojarzenia](../../../../docs/framework/data/adonet/association-end.md) określające zaangażowanych w skojarzeniu typów jednostek. Każdy punkt końcowy skojarzenia określa również [skojarzenie i liczebność](../../../../docs/framework/data/adonet/association-end-multiplicity.md) oznacza liczbę jednostek, które mogą być na końcu tego skojarzenia. Skojarzenie i liczebność może mieć wartość równą jeden (1), zero lub jeden (od 0 do 1), lub wielu (*). Jednostki na jednym końcu asocjacji jest możliwy za pośrednictwem [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md), lub za pomocą kluczy obcych, jeśli są one widoczne na typ jednostki. Aby uzyskać więcej informacji, zobacz [właściwość klucza obcego](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
 W aplikacji wystąpienia skojarzenia reprezentuje określone skojarzenia (takie jak skojarzenie między wystąpieniem odbiorcy i wystąpień zamówienia). Skojarzenie wystąpienia są logicznie pogrupowane w [zestaw skojarzeń](../../../../docs/framework/data/adonet/association-set.md). Zestawów skojarzeń (i [zestawy jednostek](../../../../docs/framework/data/adonet/entity-set.md)) są logicznie pogrupowane w [kontener jednostek](../../../../docs/framework/data/adonet/entity-container.md).  
  
## <a name="property"></a>Właściwość  
 [Typy jednostek](../../../../docs/framework/data/adonet/entity-type.md) zawierają [właściwości](../../../../docs/framework/data/adonet/property.md) definiują ich struktury i właściwości. Na przykład typ jednostki Klient może mieć właściwości, takie jak CustomerId, nazwa i adres.  
  
 Właściwości w modelu koncepcyjnym są analogiczne do właściwości zdefiniowane w klasie w programie komputera. W ten sam sposób, że właściwości w klasie określenia kształtu elementu klasy i zawierają informacje o obiektach właściwości w modelu koncepcyjnym określenia kształtu typu jednostki i zawierają informacje na temat wystąpień typu jednostki.  
  
 Właściwość może zawierać danych pierwotnych (na przykład ciąg, liczba całkowita lub wartość logiczna) lub dane strukturalne (takie jak typ złożony). Aby uzyskać więcej informacji, zobacz [modelu danych jednostki: Pierwotne typy danych](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Reprezentacje Model koncepcyjny  
 A *modelu koncepcyjnego* to reprezentacja określonej struktury niektórych danych jako jednostek i relacji. Jest jednym ze sposobów do reprezentowania modelu koncepcyjnego z diagramu. Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostki (`Book`, `Publisher`, i `Author`) i dwa powiązania (`PublishedBy` i `WrittenBy`):  
  
 ![Diagram przedstawiający modelu koncepcyjnego z trzech typów jednostek.](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 Taka reprezentacja ma jednak niektórych niedoskonałości, jeśli chodzi o przekazywania niektóre szczegóły na temat modelu. Na przykład właściwość jednostki Ustaw informacje dotyczące typu i nie są przekazywane na diagramie. Bogactwa modelu koncepcyjnego mogą być przeniesione wyraźniej języka specyficznego dla domeny (DSL). [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa DSL oparty na formacie XML o nazwie *język definicji schematu koncepcyjnego* ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniżej przedstawiono definicję CSDL modelu koncepcyjnego na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Zobacz także

- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
