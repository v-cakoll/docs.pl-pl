---
title: Korzystanie z manipulacji i bezwładności w aplikacjach XNA
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871047"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="30c76-102">Korzystanie z manipulacji i bezwładności w aplikacjach XNA</span><span class="sxs-lookup"><span data-stu-id="30c76-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="30c76-103">W tym artykule opisano, jak można użyć manipulacji i bezwładności przetwarzania w aplikacji Microsoft XNA sterowanie ruchem figur.</span><span class="sxs-lookup"><span data-stu-id="30c76-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="30c76-104">Przed przeczytaniem tego artykułu, należy się zapoznać z [omówienie manipulacji i bezwładności](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tematu i należy zapoznać się z XNA podstawowe pojęcia związane z programowaniem.</span><span class="sxs-lookup"><span data-stu-id="30c76-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="30c76-105">Aby wykonać zadania opisane w tym artykule, Twój profil XNA musi odwoływać <xref:System.Windows.Input.Manipulations> zestawie, a także musi mieć [Studio gry XNA](https://msdn.microsoft.com/library/bb200104.aspx) ([Pobierz](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) zainstalowane na komputerze tak, że Twoje Projekt może odwoływać się zestawów XNA.</span><span class="sxs-lookup"><span data-stu-id="30c76-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([download](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="30c76-106">Omówienie funkcji</span><span class="sxs-lookup"><span data-stu-id="30c76-106">Overview of Functionality</span></span>  
 <span data-ttu-id="30c76-107">W tym artykule pokazano, jak utworzyć niestandardowe klasę, która reprezentuje fragment gier, korzystającą z manipulacji i bezwładności przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="30c76-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="30c76-108">Ta klasa umożliwia Ci manipulowanie gier element na ekranie przez przeciągnięcie go za pomocą myszy, a następnie zwalniając je.</span><span class="sxs-lookup"><span data-stu-id="30c76-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="30c76-109">Po wydaniu bezwładności przetwarzania przechowuje element gier, stopniowo przeniesienia go spowalnia.</span><span class="sxs-lookup"><span data-stu-id="30c76-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="30c76-110">Ruch jest liniowych i angular.</span><span class="sxs-lookup"><span data-stu-id="30c76-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="30c76-111">![Prostej manipulacji i bezwładności aplikacji. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="30c76-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="30c76-112">Ponadto kolekcji niestandardowej utworzono, która zarządza wieloma figur.</span><span class="sxs-lookup"><span data-stu-id="30c76-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="30c76-113">Upraszcza to obsługi, która jest wymagana od klasy przeniesienie gry XNA.</span><span class="sxs-lookup"><span data-stu-id="30c76-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="30c76-114">Tworzenie klasy GamePiece</span><span class="sxs-lookup"><span data-stu-id="30c76-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="30c76-115">Tworzenie klasy GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="30c76-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="30c76-116">Tworzenie klasy Game1</span><span class="sxs-lookup"><span data-stu-id="30c76-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="30c76-117">Listy pełnego kodu</span><span class="sxs-lookup"><span data-stu-id="30c76-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="30c76-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30c76-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="30c76-119">Omówienie manipulacji i bezwładności</span><span class="sxs-lookup"><span data-stu-id="30c76-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
