---
title: 'Modelu danych jednostki: przestrzenie nazw'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 0fdb007e70b7dd2e4a812d711cb6348e3f563bad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765233"
---
# <a name="entity-data-model-namespaces"></a>Modelu danych jednostki: przestrzenie nazw
Przestrzeń nazw w modelu danych jednostki (EDM) jest abstrakcyjny kontener dla [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md), [typów złożonych](../../../../docs/framework/data/adonet/complex-type.md), i [skojarzenia](../../../../docs/framework/data/adonet/association-type.md). Przestrzenie nazw w EDM są podobne do przestrzeni nazw w języku programowania: stanowią kontekst dla obiektów, które zawierają i umożliwiają do odróżniania obiektów, które mają taką samą nazwę (ale znajdują się w różnych przestrzeniach nazw).  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący kod w pliku CSDL używa przestrzeni nazw do identyfikacji typu, który jest zdefiniowany w różnych modelu koncepcyjnego. W przykładzie zdefiniowano typ jednostki (`Publisher`) mający właściwość typu złożonego (`Address`) importowanym z `ExtendedBooksModel` przestrzeni nazw. Należy pamiętać, że `Using` element wskazuje, że przestrzeni nazw zostały zaimportowane. Należy również zauważyć, że typ `Address` właściwość jest zdefiniowana przy użyciu w pełni kwalifikowanej nazwy (`ExtendedBooksModel.Address`), co oznacza, że ten typ jest zdefiniowany w `ExtendedBooksModel` przestrzeni nazw.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
