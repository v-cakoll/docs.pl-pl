---
title: Zachowywanie odstępu podczas serializacji3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d357d40c13a66a152b3c8bb5f61e3a3374c4055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484076"
---
# <a name="preserving-white-space-while-serializing"></a>Zachowywanie białych znaków podczas serializowania
W tym temacie opisano sposób kontrolowania odstępu podczas serializacji drzewa XML.  
  
 Typowym scenariuszem jest odczyt wciętego kodu XML, utworzenie drzewa XML w pamięci bez żadnych węzłów tekstu odstępu (czyli nie zachowanie odstępu), wykonanie niektórych operacji w pliku XML, a następnie zapisanie kodu XML z wcięciem. Podczas serializacji XML z formatowaniem zachowano tylko znaczące odstępy w drzewie XML. Jest to domyślne [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zachowanie dla .  
  
 Innym typowym scenariuszem jest odczytywanie i modyfikowanie języka XML, który został już celowo wcięty. W jakikolwiek sposób możesz nie chcieć zmienić tego wcięcia. Aby to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zrobić w , należy zachować biały znak podczas ładowania lub analizowania XML i wyłączyć formatowanie podczas serializacji XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Zachowanie odstępu metod serializowania drzew XML  
 Następujące metody w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klas serializować drzewa XML. Drzewo XML można serializować do pliku, <xref:System.IO.TextReader>pliku <xref:System.Xml.XmlReader>lub pliku . Metoda `ToString` serializuje do ciągu.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Jeśli metoda nie <xref:System.Xml.Linq.SaveOptions> bierze jako argument, a następnie metoda będzie format (wcięcie) serializowany kod XML. W takim przypadku wszystkie nieistotne odstępy w drzewie XML są odrzucane.  
  
 Jeśli metoda ma <xref:System.Xml.Linq.SaveOptions> jako argument, a następnie można określić, że metoda nie format (wcięcie) serializowany chyląc XML. W takim przypadku wszystkie odstępy w drzewie XML są zachowywane.  
