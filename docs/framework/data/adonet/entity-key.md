---
title: klucz jednostki
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 1484a73450d5a435f795f18f122c7fe8494cf197
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879190"
---
# <a name="entity-key"></a>klucz jednostki
*Klucz jednostki* jest [właściwość](../../../../docs/framework/data/adonet/property.md) lub zbiór właściwości [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) które są używane w celu ustalenia tożsamości. Właściwości, które tworzą klucz jednostki są wybierane w czasie projektowania. Wartości właściwości klucza jednostki musi jednoznacznie identyfikować wystąpienia typu jednostki, w ramach [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md) w czasie wykonywania. Należy wybrać właściwości, które tworzą klucz jednostki w celu zagwarantowania unikatowości wystąpień w zestawie jednostek.  
  
 Poniżej przedstawiono wymagania dotyczące zbiór właściwości jako klucz jednostki:  
  
- Brak kluczy dwie jednostki w ramach zestawu jednostek, mogą być identyczne. Oznacza to, że dwie jednostki w ramach zestawu jednostek, aby uzyskać wartości dla wszystkich właściwości, które tworzą klucz nie może być taka sama. Jednak niektóre (ale nie wszystkie) wartości, które tworzą jednostki klucz może być taki sam.  
  
- Klucz jednostki musi składać się z szeregu innych niż null, niezmienne, [pierwotny typ właściwości](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
- Nie można zmienić właściwości, które tworzą klucz jednostki dla typu danej jednostki. Nie zezwalaj na więcej niż jeden klucz jednostki możliwe dla danej jednostki typu; zastępczy klucze nie są obsługiwane.  
  
- Gdy jednostka jest zaangażowana w hierarchii dziedziczenia, jednostkę główną musi zawierać wszystkie właściwości, które tworzą klucz jednostki, a klucz musi być zdefiniowany dla typu jednostki głównej. Aby uzyskać więcej informacji, zobacz [modelu danych jednostki: Dziedziczenie](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. Właściwości każdego typu jednostki, które tworzą klucz jednostki są oznaczone symbolem "(klucz)". Należy pamiętać, że `Author` typ jednostki ma klucz jednostki, która składa się z dwóch właściwości `Name` i `Address`.  
  
 ![Przykładowy model przy użyciu trzech typów jednostek](./media/entity-key/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje CSDL poniżej `Book` typu jednostki, które pokazano na powyższym diagramie. Należy pamiętać, że klucz jest zdefiniowana, odwołując się do `ISBN` właściwość typu jednostki.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` Właściwość jest dobrym wyborem dla klucza jednostki, ponieważ International Standard książki numer (ISBN) unikatowo identyfikuje książki.  
  
 Definiuje CSDL poniżej `Author` typu jednostki, które pokazano na powyższym diagramie. Należy pamiętać, że klucz jednostki składa się z dwóch właściwości `Name` i `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Za pomocą `Name` i `Address` jednostki klucz jest wyboru rozsądny, ponieważ dwóch autorów o takiej samej nazwie jest mało prawdopodobne na żywo na ten sam adres. Jednak ten wybór dla klucza jednostki absolutnie nie gwarantuje klucze unikatowe jednostki w zestawie jednostek. Dodawanie właściwości, takie jak `AuthorId`, który może być używany do jednoznacznego identyfikowania Autor może w tym przypadku zalecane.  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
