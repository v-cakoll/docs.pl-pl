---
title: Weryfikacja nazw elementów i atrybutów XML podczas tworzenia nowych węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 008cf14e63b8458feebf26eaf27be516bb79f933
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959046"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="391e2-102">Weryfikacja nazw elementów i atrybutów XML podczas tworzenia nowych węzłów</span><span class="sxs-lookup"><span data-stu-id="391e2-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="391e2-103">XML Document Object Model (DOM) sprawdza poprawność nazwy, podczas tworzenia nowych węzłów elementów lub węzłów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="391e2-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="391e2-104">Jeśli nazwy zawiera niedozwolone znaki, jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="391e2-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="391e2-105">Aby upewnić się, że nazwy są prawidłowe i zakodowany poprawnie, należy użyć **obiekt XmlConvert** klasy do kodowania nazwę i dekodowania go ponownie na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="391e2-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="391e2-106">**XmlWriter** posiada metody, które obsługują dodatkową pracę, aby upewnić się, generowany jest poprawnie sformułowany dokument XML.</span><span class="sxs-lookup"><span data-stu-id="391e2-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="391e2-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="391e2-107">See also</span></span>

- [<span data-ttu-id="391e2-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="391e2-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
