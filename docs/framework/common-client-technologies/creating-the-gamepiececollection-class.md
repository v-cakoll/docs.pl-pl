---
title: Tworzenie klasy GamePieceCollection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: b8b53e5890aaebbad2f0a5f0e058182193b11622
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-gamepiececollection-class"></a><span data-ttu-id="7dadf-102">Tworzenie klasy GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="7dadf-102">Creating the GamePieceCollection Class</span></span>
<span data-ttu-id="7dadf-103">**GamePieceCollection** klasa pochodzi od klasy generycznej listy i wprowadza metody ułatwia zarządzanie wieloma **GamePiece** obiektów.</span><span class="sxs-lookup"><span data-stu-id="7dadf-103">The **GamePieceCollection** class derives from the generic List class, and introduces methods to more easily manage multiple **GamePiece** objects.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="7dadf-104">Tworzenie kodu</span><span class="sxs-lookup"><span data-stu-id="7dadf-104">Creating the Code</span></span>  
 <span data-ttu-id="7dadf-105">Konstruktor obiektu **GamePieceCollection** klasy inicjuje prywatnego elementu członkowskiego *capturedIndex*.</span><span class="sxs-lookup"><span data-stu-id="7dadf-105">The constructor of the **GamePieceCollection** class initializes the private member *capturedIndex*.</span></span> <span data-ttu-id="7dadf-106">To pole służy do śledzenia mającej gier elementy są obecnie przechwytywanie myszy.</span><span class="sxs-lookup"><span data-stu-id="7dadf-106">This field is used to track which of the game pieces currently has the mouse capture.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 <span data-ttu-id="7dadf-107">**ProcessInertia** i **rysowania** metody uprościć kod potrzebne w grze [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) i [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metody Wyliczanie wszystkich figur w kolekcji i wywołanie metody odpowiednich na każdym **GamePiece** obiektu.</span><span class="sxs-lookup"><span data-stu-id="7dadf-107">The **ProcessInertia** and the **Draw** methods simplify the code needed in the game [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) and [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) methods by enumerating all of the game pieces in the collection and calling the respective method on each **GamePiece** object.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 <span data-ttu-id="7dadf-108">**UpdateFromMouse** również wywoływana jest metoda podczas aktualizacji gier.</span><span class="sxs-lookup"><span data-stu-id="7dadf-108">The **UpdateFromMouse** method is also called during game update.</span></span> <span data-ttu-id="7dadf-109">Umożliwia on tylko jeden fragment gier ma myszą przechwytywania sprawdzając najpierw, czy bieżące przechwytywanie (jeśli istnieje) jest nadal obowiązują.</span><span class="sxs-lookup"><span data-stu-id="7dadf-109">It enables only one game piece to have the mouse capture by first checking to see if the current capture (if any) is still in effect.</span></span> <span data-ttu-id="7dadf-110">Jeśli tak, figurę nie może wyszukać przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="7dadf-110">If so, no other piece is allowed to check for capture.</span></span>  
  
 <span data-ttu-id="7dadf-111">Jeśli element nie ma obecnie przechwytywania **UpdateFromMouse** metoda wylicza każda gier od ostatniej do pierwszej i sprawdza, czy dany raport myszy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="7dadf-111">If no piece currently has the capture, the **UpdateFromMouse** method enumerates each game piece from last to first, and checks to see if that piece reports a mouse capture.</span></span> <span data-ttu-id="7dadf-112">Jeśli tak, bieżący element przechwyconych staje się ten element, a żadne dalsze przetwarzanie nie ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="7dadf-112">If so, that piece becomes the current captured piece, and no further processing takes place.</span></span> <span data-ttu-id="7dadf-113">**UpdateFromMouse** metoda sprawdza najpierw ostatni element w kolekcji, tak, że jeśli dwie części są pokrywający się, z wyższej porządek uzyska przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="7dadf-113">The **UpdateFromMouse** method checks the last item in the collection first so that if two pieces are overlapped, the one with the higher Z-order will obtain the capture.</span></span> <span data-ttu-id="7dadf-114">Porządek osi nie jest jawną ani zmienić; postanowieniom wystarczy kolejność, w którym figur są dodawane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7dadf-114">Z-order is not explicit nor changeable; it is governed simply by the order in which game pieces are added to the collection.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a><span data-ttu-id="7dadf-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7dadf-115">See Also</span></span>  
 [<span data-ttu-id="7dadf-116">Manipulacje i bezwładność</span><span class="sxs-lookup"><span data-stu-id="7dadf-116">Manipulations and Inertia</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [<span data-ttu-id="7dadf-117">Korzystanie z manipulacji i bezwładności w aplikacji platformy XNA</span><span class="sxs-lookup"><span data-stu-id="7dadf-117">Using Manipulations and Inertia in an XNA Application</span></span>](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [<span data-ttu-id="7dadf-118">Tworzenie klasy GamePiece</span><span class="sxs-lookup"><span data-stu-id="7dadf-118">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [<span data-ttu-id="7dadf-119">Tworzenie klasy Game1</span><span class="sxs-lookup"><span data-stu-id="7dadf-119">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [<span data-ttu-id="7dadf-120">Listy pełnego kodu</span><span class="sxs-lookup"><span data-stu-id="7dadf-120">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)
