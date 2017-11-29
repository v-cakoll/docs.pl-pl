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
ms.openlocfilehash: c041d5d2830222f3fae09a39f1ea10eb08772388
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="28c1a-102">XML Element i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów</span><span class="sxs-lookup"><span data-stu-id="28c1a-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="28c1a-103">XML modelu DOM (Document Object) sprawdza poprawność nazwy podczas tworzenia nowych węzłów elementu lub atrybutu węzłów.</span><span class="sxs-lookup"><span data-stu-id="28c1a-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="28c1a-104">Jeśli nazwy zawierają nieprawidłowe znaki, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="28c1a-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="28c1a-105">Aby upewnić się, że nazwy są prawidłowe i zakodowanego prawidłowo, należy użyć **obiekt XmlConvert** klasy do kodowania nazwę i dekodowania go ponownie na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28c1a-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="28c1a-106">**XmlWriter** ma metody, które są dodatkowe czynności, aby upewnić się, generowany jest poprawnie sformułowany plik XML.</span><span class="sxs-lookup"><span data-stu-id="28c1a-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c1a-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28c1a-107">See Also</span></span>  
 [<span data-ttu-id="28c1a-108">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="28c1a-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
