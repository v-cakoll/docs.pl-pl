---
title: Zachowywanie białych znaków podczas ładowania lub analizowania kodu XML
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: d015c21813df2224356bb49212fe282fa5372d03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591550"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Zachowywanie białych znaków podczas ładowania lub analizowania kodu XML
W tym temacie opisano sposób kontrolowania zachowania odstępu . [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]  
  
 Typowym scenariuszem jest odczyt wciętego kodu XML, utworzenie drzewa XML w pamięci bez żadnych węzłów tekstu odstępu (czyli nie zachowanie odstępu), wykonanie niektórych operacji w pliku XML, a następnie zapisanie kodu XML z wcięciem. Podczas serializacji XML z formatowaniem zachowano tylko znaczące odstępy w drzewie XML. Jest to domyślne [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zachowanie dla .  
  
 Innym typowym scenariuszem jest odczytywanie i modyfikowanie języka XML, który został już celowo wcięty. W jakikolwiek sposób możesz nie chcieć zmienić tego wcięcia. Aby to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zrobić w , należy zachować biały znak podczas ładowania lub analizowania XML i wyłączyć formatowanie podczas serializacji XML.  
  
 W tym temacie opisano zachowanie odstępu metod, które wypełniają drzewa XML. Aby uzyskać informacje dotyczące kontrolowania odstępu podczas serializacji drzew XML, zobacz [Zachowywanie odstępu podczas serializacji](./preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Zachowanie metod wypełniających drzewa XML  
 Następujące metody w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klas wypełnić drzewo XML. Drzewo XML można wypełnić z pliku, <xref:System.IO.TextReader> <xref:System.Xml.XmlReader>pliku, , lub ciągu:  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Jeśli metoda nie <xref:System.Xml.Linq.LoadOptions> bierze jako argument, metoda nie zachowa nieznaczne biały znak.  
  
 W większości przypadków, jeśli <xref:System.Xml.Linq.LoadOptions> metoda przyjmuje jako argument, można opcjonalnie zachować nieznaczne odstęp jako węzły tekstu w drzewie XML. Jednak jeśli metoda ładuje XML <xref:System.Xml.XmlReader>z , <xref:System.Xml.XmlReader> następnie określa, czy biały znak zostanie zachowany, czy nie. Ustawienie <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> nie będzie miało wpływu.  
  
 W przypadku zachowania odstępu biały znak jest nieznaczny, a nieznaczne odstępy są wstawiane do drzewa XML jako <xref:System.Xml.Linq.XText> węzły. Jeśli biały znak nie jest zachowywany, węzły tekstu nie są wstawiane.  
  
 Drzewo XML można utworzyć przy <xref:System.Xml.XmlWriter>użyciu pliku . Węzły, które są <xref:System.Xml.XmlWriter> zapisywane do są wypełniane w drzewie. Jednak podczas tworzenia drzewa XML przy użyciu tej metody, wszystkie węzły są zachowywane, niezależnie od tego, czy węzeł jest biały znak, czy nie, czy biały znak jest znaczący, czy nie.  
  