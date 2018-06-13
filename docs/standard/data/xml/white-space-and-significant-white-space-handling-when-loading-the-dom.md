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
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="f4181-102">Biały znak i obsługa znaczący biały znak podczas ładowania modelu DOM</span><span class="sxs-lookup"><span data-stu-id="f4181-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="f4181-103">Podczas ładowania dokumentu, można ustawić opcję, aby zachować białe i Utwórz **XmlWhitespace** węzłów w drzewie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f4181-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="f4181-104">Aby utworzyć węzłów biały znak, ustaw **PreserveWhitespace** właściwości na wartość true.</span><span class="sxs-lookup"><span data-stu-id="f4181-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="f4181-105">Jeśli ustawiono właściwość **false**białe węzły nie zostały utworzone, co jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="f4181-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="f4181-106">Węzły znaczące białe znaki zawsze są zachowywane, i **XmlSignificantWhitespace** węzły zawsze zostały utworzone w pamięci w celu przedstawienia tych danych, bez względu na ustawienie **PreserveWhitespace** Flaga.</span><span class="sxs-lookup"><span data-stu-id="f4181-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="f4181-107">Jeśli dokument został załadowany z czytnika, następnie ustawienie **PreserveWhitespace** Flaga właściwości na **XmlDocument** klasy ma wpływ na tworzenie **XmlWhitespace** węzłów tylko wtedy, gdy **WhitespaceHandling** właściwość **XmlTextReader** nie jest ustawiony na **elementu WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="f4181-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="f4181-108">Jest to wartość **WhitespaceHandling** właściwość reader, który ma pierwszeństwo przed ustawieniem tę flagę na **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="f4181-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="f4181-109">Aby uzyskać więcej informacji na temat **XmlSignificantWhitespace**, zobacz <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="f4181-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4181-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4181-110">See Also</span></span>  
 [<span data-ttu-id="f4181-111">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="f4181-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
