---
title: "Biały znak i obsługa znaczący biały znak podczas ładowania modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a16f90b6d48bc2ffabfd678722fa9b6e61328cd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Biały znak i obsługa znaczący biały znak podczas ładowania modelu DOM
Podczas ładowania dokumentu, można ustawić opcję, aby zachować białe i Utwórz **XmlWhitespace** węzłów w drzewie dokumentu. Aby utworzyć węzłów biały znak, ustaw **PreserveWhitespace** właściwości na wartość true. Jeśli ustawiono właściwość **false**białe węzły nie zostały utworzone, co jest ustawieniem domyślnym. Węzły znaczące białe znaki zawsze są zachowywane, i **XmlSignificantWhitespace** węzły zawsze zostały utworzone w pamięci w celu przedstawienia tych danych, bez względu na ustawienie **PreserveWhitespace** Flaga.  
  
 Jeśli dokument został załadowany z czytnika, następnie ustawienie **PreserveWhitespace** Flaga właściwości na **XmlDocument** klasy ma wpływ na tworzenie **XmlWhitespace** węzłów tylko wtedy, gdy **WhitespaceHandling** właściwość **XmlTextReader** nie jest ustawiony na **elementu WhitespaceHandling.None**. Jest to wartość **WhitespaceHandling** właściwość reader, który ma pierwszeństwo przed ustawieniem tę flagę na **XmlDocument**. Aby uzyskać więcej informacji na temat **XmlSignificantWhitespace**, zobacz <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
