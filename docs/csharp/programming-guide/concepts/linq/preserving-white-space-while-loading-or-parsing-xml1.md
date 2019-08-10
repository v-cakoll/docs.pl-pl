---
title: Zachowywanie białych znaków podczas ładowania lub analizowania kodu XML
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 263121468b3010884c14c9e593a857d01dc253ef
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868816"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Zachowywanie białych znaków podczas ładowania lub analizowania kodu XML
W tym temacie opisano sposób sterowania zachowaniem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]białych znaków.  
  
 Typowym scenariuszem jest odczytywanie wciętych plików XML, tworzenie drzewa XML w pamięci bez jakichkolwiek białych węzłów tekstowych (to nie zachowuje białych znaków), wykonywanie niektórych operacji na pliku XML, a następnie zapisywanie kodu XML z wcięciem. Podczas serializacji pliku XML z formatowaniem zachowywana jest tylko znaczący biały znak w drzewie XML. Jest to zachowanie domyślne dla programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Inny typowy scenariusz polega na odczytaniu i zmodyfikowaniu kodu XML, który został już celowo wcięty. W żaden sposób nie trzeba zmieniać tego wcięcia. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]tym celu należy zachować biały znak podczas ładowania lub analizowania kodu XML i wyłączyć formatowanie podczas serializacji XML.  
  
 W tym temacie opisano zachowanie białych metod, które wypełniają drzewa XML. Aby uzyskać informacje o kontrolowaniu białego miejsca podczas serializacji drzew XML, zobacz [zachowywanie białych znaków podczas serializacji](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Zachowanie metod, które wypełniają drzewa XML  
 Poniższe metody w <xref:System.Xml.Linq.XElement> klasach i <xref:System.Xml.Linq.XDocument> wypełniają drzewo XML. Można wypełnić drzewo XML z pliku, a <xref:System.IO.TextReader> <xref:System.Xml.XmlReader>, a lub ciągu:  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Jeśli metoda nie przyjmuje <xref:System.Xml.Linq.LoadOptions> jako argument, metoda nie zachowuje znaczącego odstępu.  
  
 W większości przypadków, jeśli metoda przyjmuje <xref:System.Xml.Linq.LoadOptions> jako argument, można opcjonalnie zachować nieznaczące odstępy jako węzły tekstowe w drzewie XML. Jeśli jednak metoda ładuje plik XML z elementu <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReader> określa, czy biały znak zostanie zachowany, czy nie. Ustawienie <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> nie będzie miało żadnego efektu.  
  
 Przy użyciu tych metod, jeśli biały znak jest zachowywany, w drzewie XML jako <xref:System.Xml.Linq.XText> węzły zostanie wstawiony nieznaczący biały znak. Jeśli odstęp nie jest zachowywany, węzły tekstu nie są wstawiane.  
  
 Drzewo XML można utworzyć przy użyciu <xref:System.Xml.XmlWriter>. Węzły, które są zapisywane w <xref:System.Xml.XmlWriter> , są wypełniane w drzewie. Jednak podczas tworzenia drzewa XML przy użyciu tej metody wszystkie węzły są zachowywane niezależnie od tego, czy jest to biały znak, czy nie, czy biały znak jest znaczący.  
  