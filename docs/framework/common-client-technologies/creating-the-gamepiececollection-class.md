---
title: Tworzenie klasy GamePieceCollection
ms.date: 03/30/2017
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
ms.openlocfilehash: 6473f7afce1422ee31d4f1872f8310bdeeb9a3b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742143"
---
# <a name="creating-the-gamepiececollection-class"></a>Tworzenie klasy GamePieceCollection
**GamePieceCollection** klasa pochodzi od klasy generycznej listy i wprowadza metody ułatwia zarządzanie wieloma **GamePiece** obiektów.  
  
## <a name="creating-the-code"></a>Tworzenie kodu  
 Konstruktor obiektu **GamePieceCollection** klasy inicjuje prywatnego elementu członkowskiego *capturedIndex*. To pole służy do śledzenia mającej gier elementy są obecnie przechwytywanie myszy.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 **ProcessInertia** i **rysowania** metody uprościć kod potrzebne w grze [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) i [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metody Wyliczanie wszystkich figur w kolekcji i wywołanie metody odpowiednich na każdym **GamePiece** obiektu.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 **UpdateFromMouse** również wywoływana jest metoda podczas aktualizacji gier. Umożliwia on tylko jeden fragment gier ma myszą przechwytywania sprawdzając najpierw, czy bieżące przechwytywanie (jeśli istnieje) jest nadal obowiązują. Jeśli tak, figurę nie może wyszukać przechwytywania.  
  
 Jeśli element nie ma obecnie przechwytywania **UpdateFromMouse** metoda wylicza każda gier od ostatniej do pierwszej i sprawdza, czy dany raport myszy przechwytywania. Jeśli tak, bieżący element przechwyconych staje się ten element, a żadne dalsze przetwarzanie nie ma miejsce. **UpdateFromMouse** metoda sprawdza najpierw ostatni element w kolekcji, tak, że jeśli dwie części są pokrywający się, z wyższej porządek uzyska przechwytywania. Porządek osi nie jest jawną ani zmienić; postanowieniom wystarczy kolejność, w którym figur są dodawane do kolekcji.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulacje i bezwładność](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Korzystanie z manipulacji i bezwładności w aplikacjach XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Tworzenie klasy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Tworzenie klasy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [Listy pełnego kodu](../../../docs/framework/common-client-technologies/full-code-listings.md)
