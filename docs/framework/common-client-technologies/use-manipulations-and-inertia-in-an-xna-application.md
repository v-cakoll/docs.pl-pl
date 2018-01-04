---
title: "Korzystanie z manipulacji i bezwładności w aplikacjach XNA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7452a6001742bc9e0456ccb6339f13596a2ab72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="a4711-102">Korzystanie z manipulacji i bezwładności w aplikacjach XNA</span><span class="sxs-lookup"><span data-stu-id="a4711-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="a4711-103">W tym artykule opisano, jak można użyć manipulacji i bezwładności przetwarzania w aplikacji Microsoft XNA kontroli przemieszczania figur.</span><span class="sxs-lookup"><span data-stu-id="a4711-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="a4711-104">Przed przeczytaniem tego artykułu, należy się zapoznać z [omówienie manipulacji i bezwładności](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tematu i należy zapoznać się z XNA podstawowe koncepcje programowania.</span><span class="sxs-lookup"><span data-stu-id="a4711-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="a4711-105">Aby wykonać zadania opisane w tym artykule, musi odwoływać się projektu XNA <xref:System.Windows.Input.Manipulations> zestawu, a musi mieć [Studio gry XNA](http://msdn.microsoft.com/library/bb200104.aspx) ([Pobierz](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) zainstalowanej na komputerze tak, że Twoje Projekt można odwoływać się do zestawów XNA.</span><span class="sxs-lookup"><span data-stu-id="a4711-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([download](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="a4711-106">Omówienie funkcji</span><span class="sxs-lookup"><span data-stu-id="a4711-106">Overview of Functionality</span></span>  
 <span data-ttu-id="a4711-107">W tym artykule przedstawiono sposób tworzenia niestandardowych klasa, która reprezentuje gier fragment, który korzysta z manipulacji i bezwładności przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a4711-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="a4711-108">Ta klasa umożliwia manipulowania gier element na ekranie, przeciągając go za pomocą myszy, a następnie jego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="a4711-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="a4711-109">Po wydaniu bezwładności przetwarzania przechowuje element gier, przenoszenie ponieważ stopniowo spowalnia.</span><span class="sxs-lookup"><span data-stu-id="a4711-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="a4711-110">Ruch jest liniowych i kąta.</span><span class="sxs-lookup"><span data-stu-id="a4711-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="a4711-111">![Prostej manipulacji i bezwładności aplikacji. ] (../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="a4711-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="a4711-112">Ponadto kolekcji niestandardowej jest tworzony, który zarządza wiele figur.</span><span class="sxs-lookup"><span data-stu-id="a4711-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="a4711-113">Upraszcza to obsługi z klasy gry XNA jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="a4711-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="a4711-114">Tworzenie klasy GamePiece</span><span class="sxs-lookup"><span data-stu-id="a4711-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="a4711-115">Tworzenie klasy GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="a4711-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="a4711-116">Tworzenie klasy Game1</span><span class="sxs-lookup"><span data-stu-id="a4711-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="a4711-117">Listy pełnego kodu</span><span class="sxs-lookup"><span data-stu-id="a4711-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4711-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4711-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="a4711-119">Omówienie manipulacji i bezwładności</span><span class="sxs-lookup"><span data-stu-id="a4711-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
