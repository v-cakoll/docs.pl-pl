---
title: — Element XML i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 008cf14e63b8458feebf26eaf27be516bb79f933
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216044"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="d2c4f-102">— Element XML i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów</span><span class="sxs-lookup"><span data-stu-id="d2c4f-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="d2c4f-103">XML Document Object Model (DOM) sprawdza poprawność nazwy, podczas tworzenia nowych węzłów elementów lub węzłów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="d2c4f-104">Jeśli nazwy zawiera niedozwolone znaki, jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="d2c4f-105">Aby upewnić się, że nazwy są prawidłowe i zakodowany poprawnie, należy użyć **obiekt XmlConvert** klasy do kodowania nazwę i dekodowania go ponownie na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="d2c4f-106">**XmlWriter** posiada metody, które obsługują dodatkową pracę, aby upewnić się, generowany jest poprawnie sformułowany dokument XML.</span><span class="sxs-lookup"><span data-stu-id="d2c4f-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c4f-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2c4f-107">See also</span></span>

- [<span data-ttu-id="d2c4f-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="d2c4f-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
