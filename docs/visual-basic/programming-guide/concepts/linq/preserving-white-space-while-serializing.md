---
title: Zachowywanie białych znaków podczas Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e9b73089830bf7e6cb0ea9e469bf667f12c571d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396405"
---
# <a name="preserving-white-space-while-serializing"></a>Zachowywanie białych znaków podczas serializowania
W tym temacie opisano, jak sterować białym znakiem podczas serializowania drzewa XML.  
  
 Typowym scenariuszem jest odczytywanie wciętych plików XML, tworzenie drzewa XML w pamięci bez jakichkolwiek białych węzłów tekstowych (to nie zachowuje białych znaków), wykonywanie niektórych operacji na pliku XML, a następnie zapisywanie kodu XML z wcięciem. Podczas serializacji pliku XML z formatowaniem zachowywana jest tylko znaczący biały znak w drzewie XML. Jest to zachowanie domyślne dla programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Inny typowy scenariusz polega na odczytaniu i zmodyfikowaniu kodu XML, który został już celowo wcięty. W żaden sposób nie trzeba zmieniać tego wcięcia. W tym celu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] należy zachować biały znak podczas ładowania lub analizowania kodu XML i wyłączyć formatowanie podczas serializacji XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Zachowanie białych znaków metod, które serializować drzewa XML  
 Następujące metody w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klasy serializacji drzewa XML. Można serializować drzewo XML do pliku, a <xref:System.IO.TextReader> lub <xref:System.Xml.XmlReader> . `ToString`Metoda jest serializowana do ciągu.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Jeśli metoda nie przyjmuje <xref:System.Xml.Linq.SaveOptions> argumentu, metoda będzie formatować (wcięcie) serializacji XML. W takim przypadku wszystkie nieznaczące białe znaki w drzewie XML są odrzucane.  
  
 Jeśli metoda przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument, można określić, że metoda nie formatuje (wcięcie) serializacji XML. W takim przypadku wszystkie odstępy w drzewie XML są zachowywane.  
  
## <a name="see-also"></a>Zobacz też

- [Serializowanie drzew XML (Visual Basic)](serializing-xml-trees.md)
