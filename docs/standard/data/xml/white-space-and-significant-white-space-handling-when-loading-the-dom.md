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
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="79800-102">Biały znak i obsługa znaczący biały znak podczas ładowania modelu DOM</span><span class="sxs-lookup"><span data-stu-id="79800-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="79800-103">Podczas ładowania dokumentu, można ustawić opcję, aby zachować białe i Utwórz **XmlWhitespace** węzłów w drzewie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="79800-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="79800-104">Aby utworzyć węzłów biały znak, ustaw **PreserveWhitespace** właściwości na wartość true.</span><span class="sxs-lookup"><span data-stu-id="79800-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="79800-105">Jeśli ustawiono właściwość **false**białe węzły nie zostały utworzone, co jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="79800-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="79800-106">Węzły znaczące białe znaki zawsze są zachowywane, i **XmlSignificantWhitespace** węzły zawsze zostały utworzone w pamięci w celu przedstawienia tych danych, bez względu na ustawienie **PreserveWhitespace** Flaga.</span><span class="sxs-lookup"><span data-stu-id="79800-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="79800-107">Jeśli dokument został załadowany z czytnika, następnie ustawienie **PreserveWhitespace** Flaga właściwości na **XmlDocument** klasy ma wpływ na tworzenie **XmlWhitespace** węzłów tylko wtedy, gdy **WhitespaceHandling** właściwość **XmlTextReader** nie jest ustawiony na **elementu WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="79800-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="79800-108">Jest to wartość **WhitespaceHandling** właściwość reader, który ma pierwszeństwo przed ustawieniem tę flagę na **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="79800-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="79800-109">Aby uzyskać więcej informacji na temat **XmlSignificantWhitespace**, zobacz <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="79800-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79800-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79800-110">See Also</span></span>  
 [<span data-ttu-id="79800-111">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="79800-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
