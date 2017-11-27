---
title: Tworzenie klasy GamePiece
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
caps.latest.revision: "9"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 989883034b30c3ec67f5441c5512418643546519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-gamepiece-class"></a>Tworzenie klasy GamePiece
**GamePiece** klasa hermetyzuje wszystkie funkcje, które są wymagane do załadowania obrazu gier element XNA firmy Microsoft, śledzenie stanu myszy w odniesieniu do gier fragment, przechwytywanie myszy, podaj manipulacji i bezwładności przetwarzania, a zapewnienia możliwości podskakujące, gdy element gier osiągnie limitu portu widoku.  
  
## <a name="private-members"></a>Prywatne elementy członkowskie  
 W górnej części **GamePiece** klasy, kilka prywatne elementy członkowskie są zadeklarowane.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>Właściwości publiczne  
 Trzy następujące prywatne elementy członkowskie są udostępniane za pośrednictwem właściwości publiczne. **Skali** i **PieceColor** właściwości umożliwić aplikacji określają odpowiednio skali i kolor element. **Granice** właściwości jest narażony na Włącz jeden element na potrzeby renderowania, takich jak po jednej powinien nakładki innego granice innego. Poniższy kod przedstawia deklaracji właściwości publiczne.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>Konstruktor klasy  
 Konstruktor **GamePiece** klasy przyjmuje następujące parametry:  
  
-   A [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) typu. Odwołania przekazywane w tym miejscu jest przypisany do prywatnego elementu członkowskiego `spriteBatch`i jest używana do dostępu [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) metodą podczas gry element renderowany. Ponadto [GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) właściwość jest używana do tworzenia [tekstury](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) obiekt skojarzony z wystąpieniem gier oraz w celu uzyskania rozmiar portu widoku w celu wykrycia, gdy element gier napotka granice okna tak, aby element można Odbijanie.  
  
-   Ciąg określający nazwę pliku obrazu do użycia do nich gier.  
  
 Tworzy konstruktora <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> obiektu i <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> obiektu i ustanawia programy obsługi zdarzeń dla zdarzenia ich.  
  
 Poniższy kod przedstawia Konstruktor **GamePiece** klasy.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>Interakcja z myszą  
 **UpdateFromMouse** metoda jest odpowiedzialna za wykrywanie po naciśnięciu przycisku myszy, gdy wskaźnik myszy znajduje się w granicach element gier i wykrywania, kiedy zwolniono przycisk myszy.  
  
 Po naciśnięciu lewego przycisku myszy (gdy wskaźnik myszy znajduje się wewnątrz granic element), ta metoda ustawia flagę wskazują, że ten element gier zostały przechwycone myszy i rozpoczyna przetwarzanie manipulowanie.  
  
 Manipulowanie przetwarzania jest uruchomiona, tworząc tablicę <xref:System.Windows.Input.Manipulations.Manipulator2D> obiektów i przekazywanie ich do <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> obiektu. Powoduje to, że procesor manipulowania do oceny manipulatory (w tym przypadku manipulatora pojedynczego) i wywoływanie zdarzeń manipulowanie.  
  
 Ponadto punkt, w którym występuje przeciąganie zostało zapisane. Służy to później, podczas <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> zdarzenie, aby dopasować tłumaczenia zmian wartości tak, aby element gier obraca się w wierszu za punkt przeciągania.  
  
 Ponadto ta metoda zwraca stan przechwytywanie myszy. Dzięki temu [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) obiektu do zarządzania przechwytywania, gdy istnieje wiele figur.  
  
 Poniższy kod przedstawia **UpdateFromMouse** metody.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>Operacje przetwarzania  
 Po rozpoczęciu manipulowania <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> zdarzenia. Zatrzymuje program obsługi dla tego zdarzenia bezwładności przetwarzania, jeśli występuje i ustawia *processInertia* flaga `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 Jako wartości skojarzone z zmiany manipulowania <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> zdarzenia. Program obsługi dla tego zdarzenia używa wartości delta zdarzeń przekazanych argumentów wprowadzać zmiany do wartości pozycji i obrotu gier fragmentu.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 Po usunięciu wszystkich manipulatory (w tym przypadku manipulatora pojedynczego), które są skojarzone z manipulowania procesora manipulowania zgłasza <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> zdarzeń. Program obsługi dla tego zdarzenia rozpoczyna się bezwładności przetwarzania ustawiając początkowej prędkości procesora bezwładności zgłaszanych przez argumenty zdarzenia i ustawia *processInertia* flaga `true`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>Przetwarzanie bezwładności  
 Jak przetwarzanie bezwładności extrapolates nowe wartości prędkości kątowego i liniowych, współrzędne (tłumaczenie) i obracanie <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> zdarzenia. Program obsługi dla tego zdarzenia używa wartości delta zdarzeń przekazanych argumentów można zmodyfikować pozycji i obrotu element gier.  
  
 Jeśli nowe współrzędne spowodować element gier, przenoszenie poza granice portu widoku, prędkość przetwarzania bezwładności została odwrócona. Powoduje to gier element Odbijanie poza granic portu widoku, który napotkał go.  
  
 Nie można zmienić właściwości <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> obiekt uruchomionej ekstrapolacji. W związku z tym podczas wycofywania prędkość X i Y, program obsługi zdarzeń najpierw zatrzymuje bezwładności przez wywołanie metody <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> metody. Następnie przypisuje nowe wartości początkowej prędkość jako bieżące wartości prędkość (dostosowana do zachowania Gąbka) i ustawia *processInertia* flaga `true`.  
  
 Poniższy kod przedstawia programu obsługi zdarzeń dla <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> zdarzeń.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 Po zakończeniu przetwarzania bezwładności procesora bezwładności zgłasza <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> zdarzeń. Ustawia program obsługi dla tego zdarzenia *processInertia* flaga `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 Brak logiki przedstawione wykonanej do tej pory faktycznie powoduje, że ekstrapolacji bezwładności występuje. Jest to realizowane w **ProcessInertia** metody. Ta metoda, która jest wywoływana wielokrotnie z pętli gier aktualizacji ( [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) — metoda) sprawdza, czy *processInertia* flaga jest ustawiona na `true`, a jeśli tak jest, wywołuje <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> Metoda. Wywołanie tej metody ekstrapolacji powoduje, że występuje i zgłasza <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> zdarzeń.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 Element gier nie są odtwarzane faktycznie dopóki nosi nazwę jednego z przeciążeń metody rysowania. Pierwszy przeciążenie tej metody jest wywoływany cyklicznie pętlę gier rysowania ( [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metody). Powoduje to gier element z bieżącego położenia, obracanie i skale.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>Dodatkowe właściwości  
 Trzy właściwości prywatne są używane przez **GamePiece** klasy.  
  
1.  **Sygnatura czasowa** — pobiera wartość sygnatury czasowej do użycia przez procesory manipulacji i bezwładności.  
  
2.  **X** — pobiera lub ustawia współrzędną X element gier. Podczas ustawiania, można dostosować granic używane do testowania trafień i lokalizację pivot procesora manipulowanie.  
  
3.  **Y** — pobiera lub ustawia współrzędną Y element gier. Podczas ustawiania, można dostosować granic używane do testowania trafień i lokalizację pivot procesora manipulowanie.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulacje i bezwładność](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Korzystanie z manipulacji i bezwładności w aplikacji platformy XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Tworzenie klasy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)
