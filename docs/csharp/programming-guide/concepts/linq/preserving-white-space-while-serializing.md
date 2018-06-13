---
title: Zachowywanie biały znak podczas Serializing3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 48e654c2b7992544cdc2c67dfc5a5136d6a9bb33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329884"
---
# <a name="preserving-white-space-while-serializing"></a>Zachowywanie białe miejsce podczas serializowania
W tym temacie opisano, jak sterowania biały znak w przypadku serializacji drzewo XML.  
  
 Typowy scenariusz jest Odczytaj dane XML z wcięciami, utwórz drzewo XML w pamięci bez żadnych węzły tekstowe spacji (to znaczy nie zachowania biały znak), operacji na pliku XML, a następnie zapisz plik XML z wcięcia. Podczas formatowania kodu XML, tylko znaczący biały znak w drzewie XML są zachowywane. Jest to domyślne zachowanie dla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Inny typowy scenariusz polega może odczytywać i modyfikować XML, który już został celowo wcięcia. Nie można zmienić tej wcięcia w dowolny sposób. Aby to zrobić w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można zachować biały znak w przypadku obciążenia lub analizy kodu XML i wyłączyć formatowania podczas serializacji XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Zachowanie spacji metod, które zserializować drzew XML  
 Następujące metody w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klasy serializować drzewo XML. Może wykonywać serializację drzewo XML w pliku <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader>. `ToString` Metody serializuje do ciągu.  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 Jeśli metoda nie przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument, a następnie metoda sformatuje (wcięcie) serializacji XML. W takim przypadku wszystkie nieważny biały znak w drzewie XML zostaną odrzucone.  
  
 Jeżeli metoda <xref:System.Xml.Linq.SaveOptions> jako argument, a następnie można określić metody nie format serializacji XML (wcięcie). W takim przypadku wszystkie biały znak w drzewie XML są zachowywane.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja XML drzew (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
