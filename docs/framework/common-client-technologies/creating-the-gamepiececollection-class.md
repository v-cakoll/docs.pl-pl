---
title: Tworzenie klasy GamePieceCollection
ms.date: 03/30/2017
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
ms.openlocfilehash: 0a39ca479e9b370b027fcec4bcf76996e6191296
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190583"
---
# <a name="creating-the-gamepiececollection-class"></a>Tworzenie klasy GamePieceCollection
**GamePieceCollection** klasa pochodzi od klasy ogólnej listy i wprowadza metody, aby łatwiej zarządzać wieloma **GamePiece** obiektów.  
  
## <a name="creating-the-code"></a>Tworzenie kodu  
 Konstruktor obiektu **GamePieceCollection** klasy inicjuje prywatnego elementu członkowskiego *capturedIndex*. To pole służy do śledzenia mającej gier elementy obecnie przechwytywanie myszy.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 **ProcessInertia** i **Rysowanie** metody upraszczają kod potrzebny w grze [Game.Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) i [Game.Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) metod przez Wyliczanie wszystkie gier elementy w kolekcji i wywołanie odpowiedniej metody na każdym **GamePiece** obiektu.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 **UpdateFromMouse** metoda jest również nazywany podczas aktualizacji gier. Dzięki temu tylko jeden fragment gier mysz przechwytywania sprawdzając najpierw sprawdzić, czy bieżące przechwytywanie (jeśli istnieje) jest nadal obowiązują. Jeśli tak, nie inne fragment jest dozwolone pod kątem przechwytywania.  
  
 Jeśli element nie ma obecnie przechwytywania **UpdateFromMouse** metoda wylicza każdy element gier z ostatniego pierwszy i kontroli w celu sprawdzenia, jeśli danego fragmentu raporty myszy przechwytywania. Jeśli tak, ten element staje się bieżącym fragmentem przechwycone, a żadne dalsze przetwarzanie ma miejsce. **UpdateFromMouse** metoda sprawdza najpierw ostatniego elementu w kolekcji, tak, że jeśli dwa elementy są pokrywający się, z wyższym porządek osiągnie przechwytywania. Porządek nie jest jawną ani mogły być zmieniane; podlega się poprzez kolejność, w którym figur są dodawane do kolekcji.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulacje i bezwładność](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Korzystanie z manipulacji i bezwładności w aplikacjach XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Tworzenie klasy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Tworzenie klasy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [Listy pełnego kodu](../../../docs/framework/common-client-technologies/full-code-listings.md)
