---
title: klucz jednostki
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 6b4e3c6876aa3de1661d680d79caa3116550e073
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764999"
---
# <a name="entity-key"></a>klucz jednostki
*Klucz jednostki* jest [właściwości](../../../../docs/framework/data/adonet/property.md) lub zbiór właściwości [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) które są używane do określania tożsamości. Właściwości, które tworzą klucz jednostki są wybierane w czasie projektowania. Wartości właściwości klucza obiektu musi jednoznacznie identyfikować wystąpienia typu jednostki, w ramach [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md) w czasie wykonywania. Właściwości, które tworzą klucz jednostki powinna być wybrana w celu zagwarantowania unikatowości wystąpień w zestawie jednostek.  
  
 Poniżej przedstawiono wymagania dotyczące zbiór właściwości jako klucz jednostki:  
  
-   Brak kluczy dwie jednostki w zestawie jednostek mogą być identyczne. Oznacza to, na dwie jednostki w zestawie jednostek, wartości dla wszystkich właściwości, które stanowią klucza nie może być taka sama. Jednak niektóre (ale nie wszystkie) wartości, które tworzą jednostki klucza może być taka sama.  
  
-   Klucz jednostki musi składać się z zestawu wartości null, modyfikować, [właściwości typu pierwotnego](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
-   Nie można zmienić właściwości tworzące klucz jednostki dla typu danej jednostki. Nie można zezwolić więcej niż jeden klucz jednostki możliwe dla danej jednostki typu; klucze surogat nie są obsługiwane.  
  
-   Gdy jednostka jest elementem hierarchii dziedziczenia, obiekt główny musi zawierać wszystkie właściwości, które tworzą klucz jednostki, a klucz jednostki musi być zdefiniowana w ramach typu jednostki głównego. Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: dziedziczenie](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. Właściwości poszczególnych typów jednostek, które tworzą kluczem jednostki są oznaczone symbolem "(klucz)". Należy pamiętać, że `Author` typ jednostki ma klucz jednostki, która składa się z dwóch właściwości `Name` i `Address`.  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje CSDL poniżej `Book` pokazano na powyższym diagramie typu jednostki. Należy pamiętać, że klucz jest zdefiniowany za pomocą odwołań do `ISBN` właściwości typu jednostki.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` Właściwość jest dobrym rozwiązaniem w przypadku klucza jednostki, ponieważ międzynarodowej standardowe książki numer (ISBN) unikatowo identyfikuje książkę.  
  
 Definiuje CSDL poniżej `Author` pokazano na powyższym diagramie typu jednostki. Należy pamiętać, że klucz jednostki składa się z dwóch właściwości `Name` i `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Przy użyciu `Name` i `Address` dla jednostki klucz jest rozsądny wybór, ponieważ dwóch autorów o takiej samej nazwie jest mało prawdopodobne na żywo z tym samym adresem. Jednak ten wybór dla kluczem jednostki nie gwarantuje, absolutnie klucze unikatowe jednostki w zestawie jednostek. Dodawanie właściwości, takie jak `AuthorId`, który może być używany do jednoznacznego identyfikowania będzie można w takim przypadku zalecane autora.  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
