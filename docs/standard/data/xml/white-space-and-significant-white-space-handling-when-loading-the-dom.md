---
title: Biały znak i obsługa znaczący biały znak podczas ładowania modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8e2279023029b5047cc7d9b4d0d97ac1f21e3f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569073"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Biały znak i obsługa znaczący biały znak podczas ładowania modelu DOM
Podczas ładowania dokumentu, można ustawić opcję, aby zachować białe i Utwórz **XmlWhitespace** węzłów w drzewie dokumentu. Aby utworzyć węzłów biały znak, ustaw **PreserveWhitespace** właściwości na wartość true. Jeśli ustawiono właściwość **false**białe węzły nie zostały utworzone, co jest ustawieniem domyślnym. Węzły znaczące białe znaki zawsze są zachowywane, i **XmlSignificantWhitespace** węzły zawsze zostały utworzone w pamięci w celu przedstawienia tych danych, bez względu na ustawienie **PreserveWhitespace** Flaga.  
  
 Jeśli dokument został załadowany z czytnika, następnie ustawienie **PreserveWhitespace** Flaga właściwości na **XmlDocument** klasy ma wpływ na tworzenie **XmlWhitespace** węzłów tylko wtedy, gdy **WhitespaceHandling** właściwość **XmlTextReader** nie jest ustawiony na **elementu WhitespaceHandling.None**. Jest to wartość **WhitespaceHandling** właściwość reader, który ma pierwszeństwo przed ustawieniem tę flagę na **XmlDocument**. Aby uzyskać więcej informacji na temat **XmlSignificantWhitespace**, zobacz <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
