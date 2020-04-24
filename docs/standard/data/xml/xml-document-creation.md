---
title: Tworzenie dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: a12555a02b45a964ff7efcbe00e0d2cb8637474a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709988"
---
# <a name="xml-document-creation"></a>Tworzenie dokumentu XML
Istnieją dwa sposoby tworzenia dokumentu XML. Jednym ze sposobów jest utworzenie **dokumentu XmlDocument** bez parametrów. Innym sposobem jest utworzenie **dokumentu XmlDocument** i przekazanie go do XmlNameTable jako parametru. Poniższy przykład pokazuje, jak utworzyć nowy pusty **dokument XmlDocument** bez parametrów.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Po utworzeniu dokumentu można załadować go przy użyciu danych z ciągu, strumienia, adresu URL, czytnika tekstu lub klasy pochodnej **XmlReader** przy użyciu metody **Load** . Istnieje również inna metoda ładowania, Metoda **LoadXml** , która odczytuje dane XML z ciągu. Aby uzyskać więcej informacji na temat różnych metod **ładowania** , zobacz [odczytywanie dokumentu XML w modelu dom](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Istnieje Klasa o nazwie **XmlNameTable**. Ta klasa jest tabelą obiektów ciągów atomowych. Ta tabela zawiera wydajny środek dla analizatora XML, aby używać tego samego obiektu ciągu dla wszystkich powtórzonych nazw elementów i atrybutów w dokumencie XML. **XmlNameTable** jest tworzony automatycznie podczas tworzenia dokumentu, jak pokazano powyżej, i jest ładowany z atrybutami i nazwami elementów podczas ładowania dokumentu. Jeśli masz już dokument z tabelą nazw, a te nazwy byłyby przydatne w innym dokumencie, możesz utworzyć nowy dokument przy użyciu metody **Load** , która przyjmuje **XmlNameTable** jako parametr. Gdy dokument zostanie utworzony przy użyciu tej metody, używa istniejącej **XmlNameTable** ze wszystkimi atrybutami i elementami już załadowanymi do niego z innego dokumentu. Może służyć do wydajnego porównywania nazw elementów i atrybutów. Aby uzyskać więcej informacji na temat **XmlNameTable**, zobacz [porównanie obiektów przy użyciu XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Aby uzyskać informacje, <xref:System.Xml.XmlNameTable>Zobacz.  
  
## <a name="see-also"></a>Zobacz też

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
