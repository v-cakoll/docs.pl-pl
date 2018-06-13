---
title: XML Element i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de11c190310dec90bd23d044f77d0c38e3a34fcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568852"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>XML Element i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów
XML modelu DOM (Document Object) sprawdza poprawność nazwy podczas tworzenia nowych węzłów elementu lub atrybutu węzłów. Jeśli nazwy zawierają nieprawidłowe znaki, jest zwracany wyjątek. Aby upewnić się, że nazwy są prawidłowe i zakodowanego prawidłowo, należy użyć **obiekt XmlConvert** klasy do kodowania nazwę i dekodowania go ponownie na poziomie aplikacji. **XmlWriter** ma metody, które są dodatkowe czynności, aby upewnić się, generowany jest poprawnie sformułowany plik XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
