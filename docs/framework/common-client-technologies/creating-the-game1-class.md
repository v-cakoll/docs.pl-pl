---
title: Tworzenie klasy Game1
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: ad3c8bc46bec137d0baf4eeec09bcd5ec277e71a
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086664"
---
# <a name="creating-the-game1-class"></a>Tworzenie klasy Game1
Zgodnie ze wszystkich projektów Microsoft XNA pochodną klasy Game1 [Microsoft.Xna.Framework.Game](/previous-versions/windows/xna/bb197040%28v%3dxnagamestudio.41%29) klasy, która dostarcza inicjowania urządzenia podstawowych elementów graficznych, gra logiczna i renderowania kodu dla XNA gry. Klasy Game1 jest dość prosty, ponieważ większość pracy w GamePiece i GamePieceCollection klasy.  
  
## <a name="creating-the-code"></a>Tworzenie kodu  
 Prywatne składowe klasy składają się z **GamePieceCollection** obiekt do przechowywania figur, [GraphicsDeviceManager](/previous-versions/windows/xna/bb197317%28v%3dxnagamestudio.41%29) obiektu, a [SpriteBatch](/previous-versions/windows/xna/bb199034%28v%3dxnagamestudio.41%29) obiekt używany do renderowania sztuk gier.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Podczas inicjowania gier te obiekty są tworzone.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Gdy [LoadContent](/previous-versions/windows/xna/bb975766%28v%3dxnagamestudio.41%29) metoda jest wywoływana, gry elementy zostały utworzone i przypisane do **GamePieceCollection** obiektu. Istnieją dwa rodzaje figur. Współczynnik skali dla fragmentów jest nieznacznie zmienione tak, istnieje kilka mniejszych i większych niektóre elementy.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Aktualizacji](/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) metoda jest wywoływana wielokrotnie przez program XNA Framework gra jest uruchomiona. [Aktualizacji](/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) wywołania metody **ProcessInertia** i **UpdateFromMouse** metod na grę element kolekcji. Te metody są opisane w [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Rysowanie](/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) metoda jest również wywoływany wielokrotnie przez program XNA Framework gra jest uruchomiona. [Rysowanie](/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) metoda wykonuje renderowania sztuk gier, wywołując **Rysowanie** metody **GamePieceCollection** obiektu. Ta metoda została opisana w[Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulacje i bezwładność](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Korzystanie z manipulacji i bezwładności w aplikacjach XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Tworzenie klasy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Listy pełnego kodu](../../../docs/framework/common-client-technologies/full-code-listings.md)
