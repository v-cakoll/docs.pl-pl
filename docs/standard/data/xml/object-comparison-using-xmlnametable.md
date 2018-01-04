---
title: "XmlNameTable przy użyciu porównanie obiektów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f6c65581437bfb22cf771d66716b3dbb62dbafae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="object-comparison-using-xmlnametable"></a>XmlNameTable przy użyciu porównanie obiektów
**XmlDocuments**, podczas tworzenia tabeli nazwy specjalnie do tego dokumentu. Gdy XML jest ładowany do dokumentu lub nowych elementów lub atrybutów są tworzone, nazwy atrybutu i elementu są umieszczane w **XmlNameTable**. Można również utworzyć **XmlDocument** przy użyciu istniejącego **niepowtarzającymi** z innego dokumentu. Gdy **XmlDocuments** są tworzone za pomocą konstruktora, który przyjmuje **XmlNameTable** parametru dokument ma dostęp do nazwy węzła, obszary nazw i prefiksy już zapisana w  **XmlNameTable**. Niezależnie od tego, jak nazwa tabeli jest ładowany z nazwami po nazwy są przechowywane w tabeli nazw można porównywać szybko przy użyciu obiektu porównania zamiast porównania ciągu. Ciągi można również dodać do tabeli nazwy przy użyciu <xref:System.Xml.NameTable.Add%2A>. Poniższy przykładowy kod przedstawia tabeli nazw, tworzenia i ciąg **mójCiąg** dodawanych do tabeli. Po wykonaniu tej **XmlDocument** jest tworzony przy użyciu tej tabeli, a nazwy elementów i atrybutów w **Myfile.xml** są dodawane do istniejącej tabeli nazw.  
  
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
  
 W poniższym przykładzie kodu pokazano tworzenie dokumentu, dwa nowe elementy dodawany do dokumentu, który dodaje je do tabeli nazwy dokumentu, a obiekt porównania nazw.  
  
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
  
 Powyższym scenariuszu tabeli nazwy przekazywane między dwa dokumenty jest typowe w przypadku, gdy ten sam typ dokumentu jest przetwarzana, takich jak dokumenty kolejności w witrynie handlu elektronicznego, które odpowiadają typ schematu XML definition language (XSD) schemat lub dokument są powtarzane definicji (DTD) i tej samej ciągów. Przy użyciu tej samej tabeli nazw zapewnia lepszą wydajność, zgodnie z takiej samej nazwie elementu występuje w wielu dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
