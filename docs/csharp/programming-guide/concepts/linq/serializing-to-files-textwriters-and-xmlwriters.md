---
title: Serializowanie do plików, elementów TextWriter i elementów XmlWriter
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868855"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializowanie do plików, elementów TextWriter i elementów XmlWriter

Drzewa XML można serializować <xref:System.IO.File>na <xref:System.IO.TextWriter>, a <xref:System.Xml.XmlWriter>, lub .

Za pomocą <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` tej metody można serializować dowolny składnik XML, w tym i , ciąg.

Jeśli chcesz pominąć formatowanie podczas serializacji do ciągu, <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> można użyć tej metody.

Domyślnym zachowaniem podczas serializacji do pliku jest sformatowanie (wcięcia) wynikowego dokumentu XML. Po wcięciu nieznaczne odstępy w drzewie XML nie są zachowywane. Aby serializować za pomocą formatowania, należy użyć jednej z przeciążeń <xref:System.Xml.Linq.SaveOptions> następujących metod, które nie są przyjmowane jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Jeśli opcja nie wcinać i zachować nieznaczne odstępy w drzewie XML, należy użyć jednej <xref:System.Xml.Linq.SaveOptions> z przeciążeń następujących metod, które przyjmuje jako argument:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Na przykład zobacz odpowiedni temat odwołania.

## <a name="see-also"></a>Zobacz też

- [Serializujące drzewa XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
