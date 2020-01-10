---
title: Weryfikacja nazw elementów i atrybutów XML podczas tworzenia nowych węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 7c99ffa9d139d94d26c562cb1668f1b855bed32d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709949"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="550e0-102">Weryfikacja nazw elementów i atrybutów XML podczas tworzenia nowych węzłów</span><span class="sxs-lookup"><span data-stu-id="550e0-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="550e0-103">Document Object Model XML (DOM) sprawdza poprawność nazw podczas tworzenia nowych węzłów elementów lub węzłów atrybutów.</span><span class="sxs-lookup"><span data-stu-id="550e0-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="550e0-104">Jeśli nazwy zawierają niedozwolone znaki, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="550e0-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="550e0-105">Aby upewnić się, że nazwy są prawidłowe i zakodowane prawidłowo, należy użyć klasy **XmlConvert** do zakodowania nazwy i zdekodować ją z powrotem na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="550e0-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="550e0-106">Element **XmlWriter** ma metody, które wykonują dodatkowe zadania w celu zapewnienia, że generowany jest poprawnie sformułowany kod XML.</span><span class="sxs-lookup"><span data-stu-id="550e0-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="550e0-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="550e0-107">See also</span></span>

- [<span data-ttu-id="550e0-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="550e0-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
