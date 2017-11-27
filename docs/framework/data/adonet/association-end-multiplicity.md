---
title: "skojarzenie liczebność zakończenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3d6071b2dfab4a1f057c9e04b84e1163fb0a53c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="association-end-multiplicity"></a>skojarzenie liczebność zakończenia
*Skojarzenie liczebność zakończenia* definiuje liczbę [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) wystąpień, które mogą być na końcu jednego [skojarzenia](../../../../docs/framework/data/adonet/association-type.md).  
  
 Skojarzenie liczebność zakończenia może mieć jedną z następujących wartości:  
  
-   jednego (1): wskazuje danego wystąpienia typu dokładnie jednego obiektu występuje na końcu skojarzenia.  
  
-   zero lub jeden (od 0 do 1): oznacza, że na końcu skojarzenia zero lub jeden wystąpień typów jednostek.  
  
-   wiele (*): oznacza, że zero, jeden lub więcej wystąpień typów jednostek na końcu skojarzenia.  
  
 Skojarzenie często jest określony przez jego liczebność punktów końcowych skojarzenia. Na przykład jeśli końce skojarzenie Liczebność punktów jednego (1), a wiele (*), skojarzenie nazywa się skojarzenia typu jeden do wielu. W poniższym przykładzie `PublishedBy` association jest skojarzeniem jeden do wielu (wydawca publikuje wiele książek i książkę są publikowane przez jednego wydawcy). `WrittenBy` Association jest skojarzeniem wiele do wielu (książkę może mieć wielu autorów i Autor może zapisywać wiele książek).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `PublishedBy` i `WrittenBy`. Punkty końcowe skojarzenia dla `PublishedBy` są skojarzenia `Book` i `Publisher` typy jednostek. Liczebność `Publisher` punkt końcowy jest jeden (1) i liczebność `Book` punkt końcowy jest wiele (*).  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `PublishedBy` skojarzenia pokazano na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
