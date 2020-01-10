---
title: Obsługa białych znaków i istotnych białych znaków podczas ładowania modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 834644a07d790401a1131d6d901f144ef90dc495
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710027"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Obsługa białych znaków i istotnych białych znaków podczas ładowania modelu DOM
Podczas ładowania dokumentu można ustawić opcję zachowania **białych znaków i utworzyć węzły** XmlSpace w drzewie dokumentu. Aby utworzyć białe węzły, ustaw właściwość **PreserveWhitespace** na true. Jeśli właściwość jest ustawiona na **wartość false**, co oznacza, że domyślnie nie są tworzone węzły białych znaków. Wszystkie węzły białych miejsc są zawsze zachowywane, a węzły **XmlSignificantWhitespace** są zawsze tworzone w pamięci, aby reprezentować te dane, niezależnie od ustawienia flagi **PreserveWhitespace** .  
  
 Jeśli dokument jest ładowany z czytnika, ustawienie właściwości flagi **PreserveWhitespace** w klasie **XmlDocument** ma wpływ na tworzenie węzłów **xmlbiałych** tylko wtedy, gdy właściwość **WhitespaceHandling** w **XmlTextReader** nie jest ustawiona na **WhitespaceHandling. None**. Jest to wartość właściwości **WhitespaceHandling** w czytniku, która ma pierwszeństwo przed ustawieniem tej flagi w **dokumencie XmlDocument**. Aby uzyskać więcej informacji na temat **XmlSignificantWhitespace**, zobacz <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
