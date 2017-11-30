---
title: Typ jednostki
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b84ff5a55cff4548539e81b16406e234dcb43f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="entity-type"></a>Typ jednostki
*Typu jednostki* jest podstawowym blokiem opisu struktury danych z modelu danych jednostki (EDM). W modelu koncepcyjnym typem jednostki reprezentuje strukturę pojęcia najwyższego poziomu, takie jak klienci lub zamówienia. Typ jednostki jest szablon dla wystąpień typów jednostek. Każdy szablon zawiera następujące informacje:  
  
-   Unikatowa nazwa. (Wymagane).  
  
-   [Klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) zdefiniowane przez co najmniej jednej właściwości. (Wymagane).  
  
-   Dane w postaci [właściwości](../../../../docs/framework/data/adonet/property.md). (Opcjonalnie).  
  
-   [Właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) umożliwiające nawigacji z jednego [zakończenia](../../../../docs/framework/data/adonet/association-end.md) z [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) w innym celu. (opcjonalnie)  
  
 W aplikacji wystąpienia typu jednostki reprezentuje określonego obiektu (na przykład odbiorcę lub kolejność). Każde wystąpienie typu jednostki musi mieć unikatową [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) w [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md).  
  
 Dwa wystąpienia typu jednostki są traktowane jako równe tylko wtedy, gdy są tego samego typu i wartości kluczy jednostki są takie same.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`:  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Należy pamiętać, że właściwości poszczególnych typów jednostek, które tworzą kluczem jednostki są oznaczone symbolem "(klucz)".  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `Book` typu jednostki pokazano na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [aspekt](../../../../docs/framework/data/adonet/facet.md)
