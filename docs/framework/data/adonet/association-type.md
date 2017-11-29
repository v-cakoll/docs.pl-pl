---
title: "Typ powiązania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 476a92979ff0dc6292e64ce5514cc600a9dee50a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="association-type"></a>Typ powiązania
*Typ skojarzenia* (nazywanych również skojarzenie) jest podstawowym blokiem opisu relacje w modelu danych jednostki (EDM). W modelu koncepcyjnym, skojarzenie reprezentuje relację między dwiema [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) (takich jak `Customer` i `Order`). W aplikacji, wystąpienie skojarzenia reprezentuje określone skojarzenia (takie jak skojarzenie między wystąpieniem `Customer` i wystąpienie `Order`). Skojarzenie wystąpienia są logicznie pogrupowane w [zestawu skojarzeń](../../../../docs/framework/data/adonet/association-set.md).  
  
 Definicja skojarzenia zawiera następujące informacje:  
  
-   Unikatowa nazwa. (Wymagane)  
  
-   Dwa [skojarzenia](../../../../docs/framework/data/adonet/association-end.md), jeden dla poszczególnych typów jednostek w relacji. (Wymagane)  
  
    > [!NOTE]
    >  Skojarzenie nie może reprezentować relację między więcej niż dwa typy jednostek. Skojarzenie można jednak zdefiniować relację samoobsługowego, określając ten sam typ jednostki dla każdego z jego punkty końcowe skojarzenia.  
  
-   A [ograniczenia integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md). (opcjonalnie)  
  
 Koniec każdego skojarzenia należy określić [skojarzenie liczebność zakończenia](../../../../docs/framework/data/adonet/association-end-multiplicity.md) oznacza liczbę wystąpień typów jednostek, które mogą być na jednym końcu skojarzenia. Skojarzenie liczebność zakończenia może mieć wartość jednego (1), zero lub jeden (od 0 do 1) lub wielu (*). Wystąpień typów jednostek w jeden element end skojarzenia jest możliwy za pośrednictwem [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) lub kluczy obcych, jeśli są one dostępne w ramach typu jednostki. Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: klucze obce](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `PublishedBy` i `WrittenBy`. Punkty końcowe skojarzenia dla `PublishedBy` są skojarzenia `Book` i `Publisher` typy jednostek. Liczebność `Publisher` punkt końcowy jest jeden (1) i liczebność `Book` punkt końcowy jest wiele (*), informujący, że wydawca publikuje wiele książek i książkę są publikowane przez jednego wydawcy.  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `PublishedBy` skojarzenia pokazano na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
