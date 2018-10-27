---
title: Tworzenie klasy GamePiece
ms.date: 03/30/2017
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
ms.openlocfilehash: f9f08437cda685d2ec1d2d0c8d54d370d9d38341
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195882"
---
# <a name="creating-the-gamepiece-class"></a>Tworzenie klasy GamePiece
**GamePiece** klasa hermetyzuje wszystkie funkcje, które są wymagane do załadowania obrazu w element gry XNA firmy Microsoft, śledzić stan myszy w odniesieniu do gier fragment, przechwytywanie myszy, podaj manipulacji i bezwładności przetwarzania, i oferowanie możliwości odbijania, gdy element gier osiągnie limity porcie widoku.  
  
## <a name="private-members"></a>Prywatne elementy członkowskie  
 W górnej części **GamePiece** klasy są deklarowane w wielu prywatnych elementów członkowskich.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>Właściwości publiczne  
 Trzy następujące prywatne składowe są udostępniane za pośrednictwem właściwości publiczne. **Skalowania** i **PieceColor** właściwości umożliwiają aplikacji określić skalę i kolor fragment, odpowiednio. **Granice** właściwość jest uwidaczniana umożliwiające jeden fragment na potrzeby renderowania, takie jak kiedy jeden fragment powinien nakładki innego granice innego. Poniższy kod przedstawia deklarację właściwości publiczne.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>Konstruktor klasy  
 Konstruktor **GamePiece** klasy przyjmuje następujące parametry:  
  
-   A [SpriteBatch](https://docs.microsoft.com/previous-versions/windows/xna/bb199034%28v%3dxnagamestudio.41%29) typu. Odwołania przekazywane w tym miejscu jest przypisany do prywatnego członka `spriteBatch`i jest używana do dostępu [SpriteBatch.Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196426%28v%3dxnagamestudio.41%29) metody, gdy gra element renderowany. Ponadto [GraphicsDevice](https://docs.microsoft.com/previous-versions/windows/xna/bb197338%28v%3dxnagamestudio.41%29) właściwość jest używana do tworzenia [tekstury](https://docs.microsoft.com/previous-versions/windows/xna/bb199375%28v%3xnagamestudio.41%29) obiekt skojarzony z fragmentem gier oraz w celu uzyskania rozmiar porcie widoku w celu wykrycia, gdy napotka element gier granica okna tak, że fragment można Odbijanie.  
  
-   Ciąg, który określa nazwę pliku obrazu do użycia dla gier fragmentu.  
  
 Tworzy konstruktora <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> obiektu i <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> obiektu i ustanawia procedury obsługi zdarzeń dla ich zdarzeń.  
  
 Poniższy kod przedstawia Konstruktor **GamePiece** klasy.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>Interakcja z myszą  
 **UpdateFromMouse** metoda jest odpowiedzialna za wykrywanie po naciśnięciu przycisku myszy, gdy wskaźnik myszy znajduje się w granicach fragment gier i wykrywania po zwolnieniu przycisku myszy.  
  
 Po naciśnięciu lewego przycisku myszy (gdy wskaźnik myszy znajduje się wewnątrz granic fragment), ta metoda Ustawia flagi, aby wskazać, że ten element gry został przechwycony myszy i rozpoczyna przetwarzanie manipulowania.  
  
 Manipulowanie przetwarzania jest uruchomiona, tworząc tablicę <xref:System.Windows.Input.Manipulations.Manipulator2D> obiektów i przekazywania ich do <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> obiektu. To powoduje, że procesor manipulowania do oceny manipulatory (w tym przypadku manipulator pojedynczego), a także podnieść do manipulowania zdarzenia.  
  
 Ponadto punktu, w którym występuje przeciągania zostanie zapisany. Jest on używany później podczas <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> zdarzenie, aby dopasować tłumaczenia zmian wartości tak, aby element gier obraca się w wierszu za przeciągnij punkt.  
  
 Ponadto ta metoda zwraca stan przechwytywanie myszy. Dzięki temu [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) obiektów do zarządzania przechwytywania w przypadku wielu figur.  
  
 Poniższy kod przedstawia **UpdateFromMouse** metody.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>Operacje przetwarzania  
 Po rozpoczęciu manipulowania <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> zdarzenie jest wywoływane. Program obsługi dla tego zdarzenia zatrzymuje bezwładności przetwarzanie danych, jeśli występuje i ustawia *processInertia* flaga `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 Jako wartości skojarzone z zmiany manipulowania <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> zdarzenie jest wywoływane. Program obsługi dla tego zdarzenia używa wartości różnicy w zdarzeniu przekazywana argumentom do wprowadzania zmian w pozycji i obrót wartości element gier.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 Po usunięciu wszystkich manipulatory (w tym przypadku manipulator pojedynczego), które są skojarzone z manipulowania procesora manipulowania zgłasza <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> zdarzeń. Program obsługi dla tego zdarzenia rozpoczyna się bezwładności przetwarzania przez ustawienie początkowego ilościach procesora bezwładności zgłaszanych przez argumenty zdarzenia i ustawia *processInertia* flaga `true`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>Przetwarzanie bezwładności  
 Jak przetwarzanie bezwładności extrapolates nowe wartości dla platformy angular liniowego i liniowa w ilościach, współrzędne (tłumaczenia) i obrót, <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> zdarzenie jest wywoływane. Program obsługi dla tego zdarzenia używa wartości różnicy w zdarzeniu przekazywana argumentom do modyfikowania położenie i obrót fragment gier.  
  
 Jeśli nowe współrzędne spowodują pojawienie się element gier, przenoszenie poza granice portu widoku, szybkość przetwarzania bezwładności została odwrócona. Powoduje to gier fragment do rozbijać granic portu widoku, który napotkał.  
  
 Nie można zmienić właściwości <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> obiektu, gdy jest on uruchomiony ekstrapolację. W związku z tym, podczas wycofywania prędkości X lub Y programu obsługi zdarzeń najpierw zatrzymuje bezwładności przez wywołanie metody <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> metody. Następnie przypisuje nowe wartości prędkości początkowej jako bieżące wartości prędkości (dostosowana do zachowania sponge) i ustawia *processInertia* flaga `true`.  
  
 W poniższym kodzie pokazano program obsługi zdarzeń dla <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> zdarzeń.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 Po zakończeniu przetwarzania bezwładności procesora bezwładności zgłasza <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> zdarzeń. Ustawia program obsługi dla tego zdarzenia *processInertia* flaga `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 Brak logiki prezentowane do tej pory faktycznie powoduje, że ekstrapolacji bezwładności wystąpić. Jest to realizowane w **ProcessInertia** metody. Ta metoda, która jest wywoływana wielokrotnie z pętli gry aktualizacji ( [Game.Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) metoda) sprawdza, czy *processInertia* flaga jest ustawiona na `true`i jeśli tak jest, wywołuje metodę <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> Metoda. Wywołanie tej metody ekstrapolacji powoduje, że występuje i zgłasza <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> zdarzeń.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 Gry element nie jest faktycznie renderowane aż nosi nazwę jednego z przeciążeń metody rysowania. Pierwsze przeciążenie tej metody jest wywoływany wielokrotnie z pętli remis ( [Game.Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) metody). Renderuje to gier element z bieżącego położenia, obrotu i skalowania czynników.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>Dodatkowe właściwości  
 Trzy właściwości prywatne są używane przez **GamePiece** klasy.  
  
1.  **Sygnatura czasowa** — pobiera wartość znacznika czasu, który będzie używany przez procesory manipulacji i bezwładności.  
  
2.  **X** — pobiera lub ustawia współrzędną X fragment gier. Podczas ustawiania, dopasowuje granic używane do testowania trafień i lokalizację pivot procesora manipulacji.  
  
3.  **Y** — pobiera lub ustawia współrzędną Y fragment gier. Podczas ustawiania, dopasowuje granic używane do testowania trafień i lokalizację pivot procesora manipulacji.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulacje i bezwładność](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Korzystanie z manipulacji i bezwładności w aplikacjach XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Tworzenie klasy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)
