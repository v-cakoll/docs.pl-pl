---
title: "XML Element i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 36b9761cefb1dba47c88d053773c89e4312dee9d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>XML Element i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów
XML modelu DOM (Document Object) sprawdza poprawność nazwy podczas tworzenia nowych węzłów elementu lub atrybutu węzłów. Jeśli nazwy zawierają nieprawidłowe znaki, jest zwracany wyjątek. Aby upewnić się, że nazwy są prawidłowe i zakodowanego prawidłowo, należy użyć **obiekt XmlConvert** klasy do kodowania nazwę i dekodowania go ponownie na poziomie aplikacji. **XmlWriter** ma metody, które są dodatkowe czynności, aby upewnić się, generowany jest poprawnie sformułowany plik XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
