---
title: Porównanie obiektów przy użyciu tabeli XmlNameTable
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 814f5434dd0473b3b1dd613a2eba14a828c464d9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862785"
---
# <a name="object-comparison-using-xmlnametable"></a>Porównanie obiektów przy użyciu tabeli XmlNameTable
**XmlDocuments**, podczas tworzenia tabeli nazwę specjalnie do tego dokumentu. Gdy XML jest ładowany do dokumentu lub są tworzone nowe elementy lub atrybuty, nazwy atrybutu i elementu są umieszczane w **tabeli XmlNameTable**. Można również utworzyć **XmlDocument** korzystania z istniejącej **niepowtarzającymi** z innego dokumentu. Gdy **XmlDocuments** są tworzone przy użyciu konstruktora, który przyjmuje **tabeli XmlNameTable** parametru dokument ma dostęp do nazwy węzłów, przestrzenie nazw i prefiksy, które już są przechowywane w  **Tabeli XmlNameTable**. Niezależnie od tego, jak tabela nazw jest ładowany z nazwami, gdy nazwy są przechowywane w tabeli, nazwy można porównać szybko za pomocą obiektu porównania, zamiast porównywania ciągów. Ciągi mogą być również dodawane do tabeli nazwy przy użyciu <xref:System.Xml.NameTable.Add%2A>. Poniższy przykładowy kod przedstawia tabelę nazw, tworzonych i ciąg **mójCiąg** dodawane do tabeli. Po tym **XmlDocument** jest tworzony przy użyciu tej tabeli, a także nazw elementów i atrybutów w **Myfile.xml** są dodawane do istniejącej tabeli nazwy.  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 W poniższym przykładzie kodu pokazano tworzenie obiektu dokumentu, dwa nowe elementy są dodawane do dokumentu, który dodaje je do tabeli nazwę dokumentu i porównanie obiektu na nazwach.  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 Powyższym scenariuszu tabeli nazwy przekazywane między dwoma dokumentami jest typowe w przypadku, gdy ten sam typ dokumentu jest przetwarzany wielokrotnie, takich jak dokumenty w witrynie handlu elektronicznego, które są zgodne z typ schematu XML definicji język (XSD) schematu lub dokumentu Definition (DTD) i tej samej ciągi są powtarzane. Używanie taką samą tabelą nazw zapewnia zwiększenie wydajności, zgodnie z takiej samej nazwie elementu odbywa się w wielu dokumentów.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
