---
title: Zachowanie podczas ładowania lub analizowania XML1 biały znak
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 74576fbc6707607ff9b2557b0825110e32c0b897
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Zachowywanie biały znak podczas ładowania lub analiza kodu XML
W tym temacie opisano, jak można kontrolować zachowanie spacji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Typowy scenariusz jest Odczytaj dane XML z wcięciami, utwórz drzewo XML w pamięci bez żadnych białe węzły tekstowe (to znaczy nie zachowania biały znak), operacji na pliku XML, a następnie zapisz plik XML z wcięcia. Podczas formatowania kodu XML, tylko znaczący biały znak w drzewie XML są zachowywane. Jest to domyślne zachowanie dla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Inny typowy scenariusz polega może odczytywać i modyfikować XML, który już został celowo wcięcia. Nie można zmienić tej wcięcia w dowolny sposób. Aby to zrobić w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można zachować biały znak w przypadku obciążenia lub analizy kodu XML i wyłączyć formatowania podczas serializacji XML.  
  
 W tym temacie opisano zachowanie spacji metod, które wypełnić drzew XML. Informacje dotyczące sterowania biały znak, podczas serializacji XML drzewa, zobacz [zachowania biały znak podczas serializowania](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Zachowanie metody, które wypełnić drzew XML  
 Następujące metody w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klasy wypełnić drzewo XML. Drzewo składni XML z pliku, można go wypełnić <xref:System.IO.TextReader>, <xref:System.Xml.XmlReader>, lub ciągiem:  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Jeśli metoda nie przyjmuje <xref:System.Xml.Linq.LoadOptions> jako argument metody nie zachowa nieważny biały znak.  
  
 W większości przypadków, gdy metoda korzysta z <xref:System.Xml.Linq.LoadOptions> jako argument, można opcjonalnie Zachowaj nieważny biały znak jako tekst węzłów w drzewie XML. Jednak jeśli metoda Trwa ładowanie XML z <xref:System.Xml.XmlReader>, a następnie <xref:System.Xml.XmlReader> Określa, czy biały znak, zostaną zachowane, czy nie. Ustawienie <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> nie odniesie żadnego skutku.  
  
 Z tych metod, jeśli biały znak jest zachowywany, nieważny biały znak jest wstawiany drzewa XML jako <xref:System.Xml.Linq.XText> węzłów. Jeśli nie są zachowywane biały znak, nie są wstawiane węzły tekstowe.  
  
 Drzewo XML można tworzyć przy użyciu <xref:System.Xml.XmlWriter>. Węzły, które są zapisywane na <xref:System.Xml.XmlWriter> są wypełnione w drzewie. Jednak podczas kompilowania drzewo XML za pomocą tej metody, wszystkie węzły są konserwowane, niezależnie od tego, czy węzeł jest białe, czy nie, lub czy biały znak jest istotny, czy nie.  
  
## <a name="see-also"></a>Zobacz też  
 [Analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
