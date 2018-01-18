---
title: "Kluczowe założenia modelu danych jednostki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f75a4fc0e529b602aca91aa3cfd2dff35e4fe640
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="entity-data-model-key-concepts"></a>Kluczowe założenia modelu danych jednostki
Do opisania struktury danych modelu danych jednostki (EDM) używa trzech podstawowych pojęć: *typu jednostki*, *typ skojarzenia*, i *właściwości*. Są to najważniejsze pojęcia związane z opisujące struktury danych w implementacji EDM.  
  
## <a name="entity-type"></a>Typ jednostki  
 [Typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) jest podstawowym blokiem opisu struktury danych z modelu danych jednostki. W modelu koncepcyjnym, typy jednostek są tworzone na podstawie [właściwości](../../../../docs/framework/data/adonet/property.md) i opisano strukturę pojęcia najwyższego poziomu, takie jak klienci i zamówienia w aplikacji biznesowych. W ten sam sposób czy definicję klasy w program komputerowy jest szablon dla wystąpienia klasy, typ jednostki jest typem szablonu dla jednostek. Jednostka reprezentuje określonego obiektu (na przykład odbiorcę lub kolejność). Każda jednostka musi mieć unikatową [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) w [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md).  Zestaw jednostek jest kolekcja wystąpień określonego typu. Zestawy jednostek (i [ustawia skojarzenie](../../../../docs/framework/data/adonet/association-set.md)) są logicznie pogrupowane w [kontenera jednostek](../../../../docs/framework/data/adonet/entity-container.md).  
  
 Dziedziczenie jest obsługiwane z typami jednostek: oznacza to, co typ jednostki mogą pochodzić z innej. Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: dziedziczenie](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>Typ powiązania  
 [Typ skojarzenia](../../../../docs/framework/data/adonet/association-type.md) (nazywanych również skojarzenie) jest podstawowym blokiem opisu relacje w modelu danych jednostki. W modelu koncepcyjnym skojarzenie reprezentuje relację między dwoma typami jednostek (na przykład klienta i zamówienia). Każde skojarzenie ma dwa [skojarzenia](../../../../docs/framework/data/adonet/association-end.md) określające objętego skojarzenia typów jednostek. Każdy end skojarzenia określa również [skojarzenie liczebność zakończenia](../../../../docs/framework/data/adonet/association-end-multiplicity.md) wskazujące, liczba jednostek, które mogą być na tym końcu skojarzenia. Skojarzenie liczebność zakończenia może mieć wartość jednego (1), zero lub jeden (od 0 do 1) lub wielu (*). Jednostki w jeden element end skojarzenia jest możliwy za pośrednictwem [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md), lub za pomocą kluczy obcych, jeśli są one dostępne w ramach typu jednostki. Aby uzyskać więcej informacji, zobacz [właściwości kluczy obcych](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
 W aplikacji wystąpienie skojarzenia reprezentuje określone skojarzenia (takie jak skojarzenie między wystąpienie klienta i wystąpień kolejności). Skojarzenie wystąpienia są logicznie pogrupowane w [zestawu skojarzeń](../../../../docs/framework/data/adonet/association-set.md). Ustawia skojarzenie (i [zestawów jednostek](../../../../docs/framework/data/adonet/entity-set.md)) są logicznie pogrupowane w [kontenera jednostek](../../../../docs/framework/data/adonet/entity-container.md).  
  
## <a name="property"></a>Właściwość  
 [Typy jednostek](../../../../docs/framework/data/adonet/entity-type.md) zawierają [właściwości](../../../../docs/framework/data/adonet/property.md) definiującą ich struktury i właściwości. Na przykład typ jednostki klienta może mieć właściwości, takie jak CustomerId, nazwa i adres.  
  
 Właściwości w modelu koncepcyjnym są analogiczne do właściwości zdefiniowane w klasie w programie komputera. W ten sam sposób, że właściwości dla klasy, zdefiniuj kształtu klasy i zawiera informacje o obiektach właściwości w modelu koncepcyjnym zdefiniuj kształtu typu jednostki i zawiera informacje na temat wystąpień typu jednostki.  
  
 Właściwość może zawierać danych pierwotnych (na przykład ciągiem, liczbą całkowitą lub wartość logiczną) lub dane strukturalne (takie jak typ złożony). Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: typy pierwotne danych](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Reprezentacje Model koncepcyjny  
 A *modelu koncepcyjnego* jest reprezentację określonej struktury niektóre dane jako jednostki i relacje. Jest jednym ze sposobów reprezentują modelu koncepcyjnego z diagramu. Poniższy diagram przedstawia model koncepcyjny z trzech typów jednostek (`Book`, `Publisher`, i `Author`) i dwa powiązania (`PublishedBy` i `WrittenBy`):  
  
 ![Modelu z właściwości nawigacji](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 Reprezentacja ta ma jednak niektóre niedociągnięć po przejściu do przekazywania niektóre szczegóły na temat modelu. Na przykład właściwości jednostki zestaw informacje dotyczące typu i nie są przekazywane na diagramie. Głębia model koncepcyjny mogą być przeniesione dokładniej języka specyficznego dla domeny (DSL). [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa DSL opartych na języku XML o nazwie *języka definicji schematu koncepcyjnego* ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniżej znajduje się definicja CSDL modelu koncepcyjnego na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Zobacz też  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
