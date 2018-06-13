---
title: Tworzenie dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ab7632966cd2a0087a8bdc1d452d02543edbec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572791"
---
# <a name="xml-document-creation"></a>Tworzenie dokumentu XML
Istnieją dwa sposoby tworzenia dokumentu XML. Jednym ze sposobów jest utworzenie **XmlDocument** bez parametrów. Innym sposobem jest utworzenie **XmlDocument** i przekaż go XmlNameTable jako parametr. Poniższy przykład pokazuje, jak utworzyć nowy, pusty **XmlDocument** przy użyciu bez parametrów.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Po utworzeniu dokumentu, będzie można go załadować z danymi z ciągu, strumienia, adres URL, czytnika tekstu lub **XmlReader** pochodzi z klasy przy użyciu **załadować** — metoda. Istnieje również innej metody load, **działanie metody LoadXML** metodę, która odczytuje z ciągu XML. Aby uzyskać więcej informacji na temat różnych **obciążenia** metod, zobacz [odczytywanie dokumentu XML do modelu DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Brak klasy o nazwie **XmlNameTable**. Ta klasa jest tabeli obiektów atomized ciągu. Ta tabela zawiera skuteczne dla analizatora składni XML do użycia z tym samym obiektem ciąg wszystkie powtórzone elementu i nazwach atrybutów w dokumencie XML. **XmlNameTable** jest tworzony automatycznie podczas dokumentu jest tworzony, jak pokazano powyżej i został załadowany z nazwami atrybutów i elementów, podczas ładowania dokumentu. Jeśli masz już dokument z tabeli nazw i nazwy, które będą przydatne w innym dokumencie, można utworzyć nowego dokumentu przy użyciu **obciążenia** metody pobierającej **XmlNameTable** jako parametr. Po utworzeniu dokumentu przy użyciu tej metody wykorzystuje istniejące **XmlNameTable** ze wszystkimi atrybuty i elementy już załadowany do niego z innego dokumentu. Może służyć do porównywania wydajnie nazw elementów i atrybutów. Aby uzyskać więcej informacji na temat **XmlNameTable**, zobacz [XmlNameTable przy użyciu porównania obiektu](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Aby informacje, zobacz <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
