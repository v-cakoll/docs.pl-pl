---
title: "Serializacja do plików, TextWriters i XmlWriters1"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2207ee3cf5bf1c89a01ba14875e788ceb53b01c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializacja do plików, TextWriters i XmlWriters
Może wykonywać serializację drzew XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.  
  
 Może wykonywać serializację jakiegokolwiek składnika XML w tym <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement>, ciąg przy użyciu `ToString` — metoda.  
  
 Jeśli chcesz pominąć formatowania podczas serializowania na ciąg, możesz użyć <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.  
  
 Thedefault zachowanie podczas serializowania do pliku ma format dokumentu (wcięcie) wynikowy kod XML. Gdy wcięcie, nieważny biały znak w drzewie XML nie są zachowywane. Do serializacji z formatowaniem, użyj jednej z przeciążeń następujących metod, które nie przyjmują <xref:System.Xml.Linq.SaveOptions> jako argument:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Opcja nie wcięcie i Zachowaj nieważny biały znak w drzewie XML, użyć jednego z przeciążeń z następujących metod, które przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Przykłady zobacz temat odpowiednie informacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja XML drzew (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
