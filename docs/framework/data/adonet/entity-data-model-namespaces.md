---
title: 'Model danych jednostki: Namespaces'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: aa11902ece5197905c20e7e572562643c57f51c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590110"
---
# <a name="entity-data-model-namespaces"></a>Model danych jednostki: Namespaces
Przestrzeń nazw w Entity Data Model (EDM) jest abstrakcyjną kontener dla [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md), [typy złożone](../../../../docs/framework/data/adonet/complex-type.md), i [skojarzenia](../../../../docs/framework/data/adonet/association-type.md). Przestrzenie nazw EDM są podobne do przestrzeni nazw w języku programowania: zapewniają kontekstu dla obiektów, które zawierają i zapewniają one sposób do odróżniania obiektów, które mają taką samą nazwę (ale znajdują się w różnych obszarach nazw).  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy kod CSDL używa przestrzeni nazw do identyfikowania typu, który jest zdefiniowany w różnych modelu koncepcyjnego. W przykładzie zdefiniowano typ jednostki (`Publisher`) zawierający właściwości typu złożonego (`Address`), została zaimportowana z `ExtendedBooksModel` przestrzeni nazw. Należy pamiętać, że `Using` element wskazuje, że został zaimportowany przestrzeni nazw. Należy również zauważyć, że typ `Address` właściwość jest zdefiniowana za pomocą jego w pełni kwalifikowana nazwa (`ExtendedBooksModel.Address`), który wskazuje, że ten typ jest zdefiniowany w `ExtendedBooksModel` przestrzeni nazw.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Zobacz także
- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
