---
title: Tworzenie klasy Game1
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: 368da9df4dffc7017abb02888bc2eb2641f04b8b
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006681"
---
# <a name="creating-the-game1-class"></a>Tworzenie klasy Game1
Zgodnie ze wszystkich projektów Microsoft XNA pochodną klasy Game1 [Microsoft.Xna.Framework.Game](https://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) klasy, która dostarcza inicjowania urządzenia podstawowych elementów graficznych, gra logiczna i renderowania kodu dla XNA gry. Klasy Game1 jest dość prosty, ponieważ większość pracy w GamePiece i GamePieceCollection klasy.  
  
## <a name="creating-the-code"></a>Tworzenie kodu  
 Prywatne składowe klasy składają się z **GamePieceCollection** obiekt do przechowywania figur, [GraphicsDeviceManager](https://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) obiektu, a [SpriteBatch](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) obiekt używany do renderowania sztuk gier.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Podczas inicjowania gier te obiekty są tworzone.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Gdy [LoadContent](https://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) metoda jest wywoływana, gry elementy zostały utworzone i przypisane do **GamePieceCollection** obiektu. Istnieją dwa rodzaje figur. Współczynnik skali dla fragmentów jest nieznacznie zmienione tak, istnieje kilka mniejszych i większych niektóre elementy.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Aktualizacji](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metoda jest wywoływana wielokrotnie przez program XNA Framework gra jest uruchomiona. [Aktualizacji](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) wywołania metody **ProcessInertia** i **UpdateFromMouse** metod na grę element kolekcji. Te metody są opisane w [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Rysowanie](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metoda jest również wywoływany wielokrotnie przez program XNA Framework gra jest uruchomiona. [Rysowanie](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metoda wykonuje renderowania sztuk gier, wywołując **Rysowanie** metody **GamePieceCollection** obiektu. Ta metoda została opisana w[Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulacje i bezwładność](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Korzystanie z manipulacji i bezwładności w aplikacjach XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Tworzenie klasy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Listy pełnego kodu](../../../docs/framework/common-client-technologies/full-code-listings.md)
