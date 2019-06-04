---
title: Serializowanie do plików, elementów TextWriter i XmlWriters1
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: c74dc7f429e4ae27f08f7acb6b3a6c39161aac71
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483548"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializowanie do plików, elementów TextWriter i elementów XmlWriter

Może wykonywać serializację drzew XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.

Może wykonywać serializację dowolny składnik XML w tym <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement>, na ciąg przy użyciu `ToString` metody.

Jeśli chcesz pominąć formatowania podczas serializowania na ciąg, możesz użyć <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.

Domyślnym zachowaniem podczas serializacji do pliku jest formatowanie dokumentu (wcięcie) wynikowy kod XML. Możesz wciąć nieważny biały znak w drzewie XML nie zostaną zachowane. Do serializacji, za pomocą formatowania, użyj jednego z przeciążeń, które z poniższych metod, które nie przyjmują <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Opcja nie twórz wcięcia i Zachowaj nieważny biały znak w drzewie XML, użyć jednego z przeciążeń z następujących metod, które przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Przykłady zobacz temat odpowiednie odwołania.

## <a name="see-also"></a>Zobacz także

- [Serializowanie drzew XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
