---
title: Serializowanie do plików, elementów TextWriter i elementów XmlWriter
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868855"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializowanie do plików, elementów TextWriter i elementów XmlWriter

Można serializować drzewa XML do <xref:System.IO.File>, a <xref:System.IO.TextWriter>lub <xref:System.Xml.XmlWriter>.

Można serializować dowolny składnik XML, w tym <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement>, do ciągu przy użyciu `ToString` metody.

Jeśli chcesz pominąć formatowanie podczas serializacji do ciągu, możesz użyć <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.

Zachowanie domyślne podczas serializowania do pliku ma format (wcięcie) otrzymany dokument XML. W przypadku wcięcia nie jest zachowywany znaczący biały znak w drzewie XML. Aby serializować z formatowaniem, użyj jednego z przeciążeń następujących metod, które nie przyjmują <xref:System.Xml.Linq.SaveOptions> argumentu:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Jeśli chcesz, aby opcja nie była wcięty i aby zachować nieznaczący biały znak w drzewie XML, użyj jednego z przeciążeń następujących metod, które przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Przykłady znajdują się w odpowiednim temacie.

## <a name="see-also"></a>Zobacz także

- [Serializowanie drzew XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
