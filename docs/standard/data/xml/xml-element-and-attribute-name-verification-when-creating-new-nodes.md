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
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="131fe-102">XML Element i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów</span><span class="sxs-lookup"><span data-stu-id="131fe-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="131fe-103">XML modelu DOM (Document Object) sprawdza poprawność nazwy podczas tworzenia nowych węzłów elementu lub atrybutu węzłów.</span><span class="sxs-lookup"><span data-stu-id="131fe-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="131fe-104">Jeśli nazwy zawierają nieprawidłowe znaki, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="131fe-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="131fe-105">Aby upewnić się, że nazwy są prawidłowe i zakodowanego prawidłowo, należy użyć **obiekt XmlConvert** klasy do kodowania nazwę i dekodowania go ponownie na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="131fe-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="131fe-106">**XmlWriter** ma metody, które są dodatkowe czynności, aby upewnić się, generowany jest poprawnie sformułowany plik XML.</span><span class="sxs-lookup"><span data-stu-id="131fe-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131fe-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="131fe-107">See Also</span></span>  
 [<span data-ttu-id="131fe-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="131fe-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
