---
title: "Właściwość klucza obcego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 044be77cbbd8b5ad16cfbd5bbf1fdde984a060d5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="foreign-key-property"></a>Właściwość klucza obcego
A *właściwości kluczy obcych* w modelu danych jednostki (EDM) jest typem pierwotnym [właściwości](../../../../docs/framework/data/adonet/property.md) (lub zestaw właściwości typu pierwotnego) na [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) zawierający [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) innego typu jednostki.  
  
 Właściwości klucza obcego jest odpowiednikiem kolumny klucza obcego w relacyjnej bazie danych. W ten sam sposób, że kolumny klucza obcego są używane w relacyjnej bazie danych można utworzyć relacji między wierszy w tabelach, kluczy obcych w modelu koncepcyjnym są używane do ustanawiania [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) między typami jednostek. A [ograniczenia integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) służy do definiowania skojarzenia między dwoma typami jednostek, gdy jeden z typów ma właściwości klucza obcego.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. `Book` Typ jednostki ma właściwości, `PublisherId`, który odwołuje się klucz `Publisher` typ jednostki po zdefiniowaniu ograniczenie integralności referencyjnej na `PublishedBy` skojarzenia.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL używa właściwości kluczy obcych `PublisherId` definiowania ograniczenie integralności referencyjnej w `PublishedBy` skojarzenia wyświetlany w modelu koncepcyjnym przedstawionych powyżej.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
