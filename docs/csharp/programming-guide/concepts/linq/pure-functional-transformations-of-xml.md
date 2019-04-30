---
title: Czyste Przekształcanie funkcjonalne kodu XML (C#)
ms.date: 07/20/2015
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
ms.openlocfilehash: d3da72e890eac92675d7eccc7fbc871249912a6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61681588"
---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="8fdc4-102">Czyste Przekształcanie funkcjonalne kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8fdc4-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="8fdc4-103">Ta sekcja zawiera samouczek Przekształcanie funkcjonalne dla formatu XML.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="8fdc4-104">W tym wyjaśnienia główne pojęcia i konstrukcji językowych należy poznać przekształceń funkcjonalnych i przykłady użycia przekształceń funkcjonalnych do manipulowania dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="8fdc4-105">Chociaż ten samouczek zawiera LINQ do XML przykłady kodu, wszystkie podstawowe pojęcia mają zastosowanie również do innych technologii LINQ.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="8fdc4-106">[Samouczka: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek zawiera szereg przykładów, każdy rozwijając poprzedni.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="8fdc4-107">Przykłady te pokazują czystego funkcjonalności innowacyjne podejście do manipulowania XML.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="8fdc4-108">Ten samouczek zakłada praktyczną wiedzę na temat języka C#.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="8fdc4-109">Nie podano szczegółowe semantykę konstrukcji językowych w tym samouczku, ale podano linki do dokumentacji języka zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="8fdc4-110">Również założono praktyczną wiedzę na temat pojęć związanych z komputerów podstawowych nauki oraz XML, w tym w przypadku przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fdc4-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8fdc4-111">In This Section</span></span>  
  
|<span data-ttu-id="8fdc4-112">Temat</span><span class="sxs-lookup"><span data-stu-id="8fdc4-112">Topic</span></span>|<span data-ttu-id="8fdc4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8fdc4-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8fdc4-114">Wprowadzenie do czystych przekształceń funkcjonalnych (C#)</span><span class="sxs-lookup"><span data-stu-id="8fdc4-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="8fdc4-115">W tym artykule opisano przekształceń funkcjonalnych i definiuje istotne terminologii.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="8fdc4-116">Samouczek: Łączenie łańcuchowe zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="8fdc4-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="8fdc4-117">W tym artykule opisano opóźnieniem i wykonanie odroczone szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="8fdc4-118">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="8fdc4-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="8fdc4-119">Samouczek, który pokazuje Przekształcanie funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8fdc4-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fdc4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fdc4-120">See also</span></span>

- [<span data-ttu-id="8fdc4-121">Tworzenie zapytań drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8fdc4-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
