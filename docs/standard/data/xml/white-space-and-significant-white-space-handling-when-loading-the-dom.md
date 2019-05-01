---
title: Obsługa białych znaków i istotnych białych znaków podczas ładowania modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d9bbb14320b84a6d417c5c28026b169092de219
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799336"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="e65fe-102">Obsługa białych znaków i istotnych białych znaków podczas ładowania modelu DOM</span><span class="sxs-lookup"><span data-stu-id="e65fe-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="e65fe-103">Podczas ładowania dokumentu, można ustawić opcję zachowania biały znak i utworzyć **XmlWhitespace** węzłów w drzewie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e65fe-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="e65fe-104">Aby utworzyć węzły odstępu, ustaw **PreserveWhitespace** właściwości na wartość true.</span><span class="sxs-lookup"><span data-stu-id="e65fe-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="e65fe-105">Jeśli ustawiono właściwość **false**biały znak węzły nie są tworzone, co jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="e65fe-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="e65fe-106">Węzły znaczące spacje są zawsze zachowywane, a **XmlSignificantWhitespace** węzły są zawsze tworzone w pamięci w celu przedstawienia tych danych, niezależnie od ustawienia **PreserveWhitespace** Flaga.</span><span class="sxs-lookup"><span data-stu-id="e65fe-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="e65fe-107">Jeśli dokument jest ładowany z czytnika, następnie ustawienie **PreserveWhitespace** flagą właściwości **XmlDocument** klasa ma wpływ na tworzenie **XmlWhitespace** węzłów tylko wtedy, gdy **WhitespaceHandling** właściwość **klasy XmlTextReader** nie jest ustawiony na **elementu WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="e65fe-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="e65fe-108">Jest to wartość z **WhitespaceHandling** właściwości czytnika, który ma pierwszeństwo przed ustawieniem tej flagi na **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="e65fe-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="e65fe-109">Aby uzyskać więcej informacji na temat **XmlSignificantWhitespace**, zobacz <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="e65fe-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e65fe-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e65fe-110">See also</span></span>

- [<span data-ttu-id="e65fe-111">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="e65fe-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
