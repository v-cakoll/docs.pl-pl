---
title: Tworzenie klasy Game1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7453c4f650e2dcadd3b8fac27b66f4db97fa0136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-game1-class"></a>Tworzenie klasy Game1
Jak z wszystkich projektów Microsoft XNA pochodną klasy Game1 [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) klasy, która dostarcza inicjowania urządzenia podstawowe grafiki, gier logiki i renderowania kodu dla platformy XNA gier. Klasy Game1 jest dość proste, ponieważ większość pracy w GamePiece i GamePieceCollection klasy.  
  
## <a name="creating-the-code"></a>Tworzenie kodu  
 Prywatne elementy członkowskie klasy składają się z **GamePieceCollection** obiektu do przechowywania figur, [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) obiektu, a [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) obiekt używany do renderowania figur.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Podczas inicjowania gier te obiekty są tworzone.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Gdy [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) metoda jest wywoływana, figur są tworzone i przypisywane do **GamePieceCollection** obiektu. Istnieją dwa typy figur. Współczynnik skali dla części zostanie zmieniona nieco, które są niektóre mniejsze lub większe niektóre elementy.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Aktualizacji](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metoda jest wywoływana wielokrotnie przez program XNA Framework gry jest uruchomiona. [Aktualizacji](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) wywołania metody **ProcessInertia** i **UpdateFromMouse** metody gry element kolekcji. Te metody są opisane w [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Rysowania](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metody jest również nazywany wielokrotnie przez program XNA Framework gry jest uruchomiona. [Rysowania](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metoda przeprowadza renderowanie figur wywołując **rysowania** metody **GamePieceCollection** obiektu. Ta metoda została opisana w[Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulacje i bezwładność](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Korzystanie z manipulacji i bezwładności w aplikacjach XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Tworzenie klasy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Listy pełnego kodu](../../../docs/framework/common-client-technologies/full-code-listings.md)
