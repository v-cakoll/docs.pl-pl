---
title: 'Entity Data Model: przestrzenie nazw'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: a403bcd459005ed9cea4a455fcde40c31c8caac9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738441"
---
# <a name="entity-data-model-namespaces"></a>Entity Data Model: przestrzenie nazw
Przestrzeń nazw w Entity Data Model (EDM) jest kontenerem abstrakcyjnym dla [typów jednostek](entity-type.md), [typów złożonych](complex-type.md)i [skojarzeń](association-type.md). Przestrzenie nazw w modelu EDM są podobne do przestrzeni nazw w języku programowania: zawierają kontekst dla obiektów, które zawierają i umożliwiają rozróżnianie obiektów, które mają taką samą nazwę (ale znajdują się w różnych obszarach nazw).  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Poniższy kod CSDL używa przestrzeni nazw do identyfikowania typu, który jest zdefiniowany w innym modelu koncepcyjnym. W przykładzie zdefiniowano typ jednostki (`Publisher`), który ma właściwość typu złożonego (`Address`) importowaną z przestrzeni nazw `ExtendedBooksModel`. Należy zauważyć, że element `Using` wskazuje, że przestrzeń nazw została zaimportowana. Należy również zauważyć, że typ właściwości `Address` jest zdefiniowany przy użyciu jej w pełni kwalifikowanej nazwy (`ExtendedBooksModel.Address`), co oznacza, że ten typ jest zdefiniowany w przestrzeni nazw `ExtendedBooksModel`.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
