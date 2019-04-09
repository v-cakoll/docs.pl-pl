---
title: 'Przewodnik: Tworzenie przycisku przy użyciu programu Microsoft Expression Blend'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: f969e13ba50c2aadd170bdb28716213056d62cad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100122"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Przewodnik: Tworzenie przycisku przy użyciu programu Microsoft Expression Blend
Ten przewodnik przeprowadzi Cię przez proces tworzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dostosowany przycisk przy użyciu Microsoft Expression Blend.  
  
> [!IMPORTANT]
>  Microsoft Expression Blend działa, generując [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , są następnie kompilowane do spraw, że program wykonywalny. Jeśli wolisz czy pracujesz z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bezpośrednio, istnieje inny przewodnik, który tworzy tej samej aplikacji jako jedna używa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] za pomocą programu Visual Studio, a nie w programie Blend. Zobacz [tworzenie przycisku przy użyciu XAML](walkthrough-create-a-button-by-using-xaml.md) Aby uzyskać więcej informacji.  
  
 Na poniższej ilustracji przedstawiono dostosowany przycisk tworzone.  
  
 ![Dostosowany przycisk, który spowoduje utworzenie](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Konwertowanie kształtu do przycisku  
 W pierwszej części tego przewodnika, możesz utworzyć niestandardowy wygląd niestandardowy przycisk. Aby to zrobić, należy najpierw przekonwertuj prostokąta przycisku. Następnie dodasz inne kształty do szablonu przycisku, tworzenie bardziej złożonych wyglądających przycisku. Dlaczego nie rozpoczynać zwykły przycisk i go dostosowywać? Ponieważ przycisk ma wbudowaną funkcję, która nie ma potrzeby; przycisków niestandardowych łatwiej jest rozpocząć prostokąta.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Aby utworzyć nowy projekt w programie Expression Blend  
  
1.  Rozpocznij Expression Blend. (Kliknij **Start**, wskaż polecenie **wszystkie programy**, wskaż polecenie **Microsoft Expression**, a następnie kliknij przycisk **Microsoft Expression Blend**.)  
  
2.  Maksymalizuj aplikacji, jeśli to konieczne.  
  
3.  Na **pliku** menu, kliknij przycisk **nowy projekt**.  
  
4.  Wybierz **standardowej aplikacji (.exe)**.  
  
5.  Nadaj projektowi nazwę `CustomButton` i naciśnij klawisz **OK**.  
  
 W tym momencie masz blank [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projektu. Można nacisnąć klawisz F5, aby uruchomić aplikację. Zgodnie z oczekiwaniami, aplikacja składa się z puste okno. Następnie Utwórz prostokąt zaokrąglony i przekonwertować go na przycisku.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Aby przekonwertować prostokąta przycisku  
  
1.  **Ustaw właściwość tło okna na czarny:** Kliknij pozycję Wybierz okno **karta właściwości**i ustaw <xref:System.Windows.Controls.Control.Background%2A> właściwość `Black`.  
  
     ![Jak ustawić tło przycisku na czarny](./media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2.  **Rysuj prostokąt około rozmiar przycisku w oknie:** Wybierz Prostokąt-narzędzie w panelu po lewej stronie narzędzia, a następnie przeciągnij prostokąt na okna.  
  
     ![Jak narysować prostokąt](./media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3.  **Zaokrąglanie narożników prostokąta — limit:** Przeciągnij punkty kontrolne, prostokąta lub ustawić bezpośrednio <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości. Ustaw wartości <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> do 20.  
  
     ![Jak narożników prostokąt zaokrąglony](./media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4.  **Zmień prostokąt na przycisku:** Zaznacz prostokąt. Na **narzędzia** menu, kliknij przycisk **wprowadzić przycisk**.  
  
     ![Jak utworzyć kształt do przycisku](./media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5.  **Określ zakres styl/szablonu:** Zostanie wyświetlone okno dialogowe, jak pokazano poniżej.  
  
     ![W oknie dialogowym "Tworzenie zasobu stylu"](./media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     Aby uzyskać **Nazwa zasobu (klucz)**, wybierz opcję **Zastosuj do wszystkich**.  To spowoduje, że wynikowy styl i szablon przycisku Zastosuj do wszystkich obiektów, które są przyciski. Aby uzyskać **zdefiniować w**, wybierz opcję **aplikacji**. To spowoduje, że wynikowy styl i przycisk szablonu mają zakres całej aplikacji. Po ustawieniu wartości w tych dwóch polach styl przycisku i szablon mają zastosowanie do wszystkich przycisków w całej aplikacji i dowolnego przycisku, który zostanie utworzony w aplikacji będą domyślnie, użyj tego szablonu.  
  
## <a name="edit-the-button-template"></a>Edytowanie szablonu przycisku  
 Masz teraz prostokąt, który został zmieniony na przycisku. W tej sekcji możesz zmodyfikować szablon przycisku i jeszcze bardziej dostosować, jak to wygląda.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Aby edytować szablon przycisku w celu zmiany wyglądu przycisku  
  
1.  **Przejdź do widoku szablonu edycji:** Dalsze dostosowywanie wyglądu przycisku, należy edytować szablon przycisku. Ten szablon został utworzony po przekonwertowaniu możemy prostokąt, aby na przycisku. Aby edytować szablon przycisku, kliknij prawym przyciskiem myszy przycisk, a następnie wybierz **Edytuj części kontrolki (szablon)** i następnie **Edytuj szablon**.  
  
     ![Jak edytować szablon](./media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     W edytorze szablonu, zwróć uwagę, czy przycisk jest teraz podzielona <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Controls.ContentPresenter>. <xref:System.Windows.Controls.ContentPresenter> Służy do prezentowania zawartości w ramach przycisku (na przykład ciąg "Button"). Zarówno prostokąt i <xref:System.Windows.Controls.ContentPresenter> są ułożone wewnątrz <xref:System.Windows.Controls.Grid>.  
  
     ![Składniki w prezentacji prostokąta](./media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2.  **Zmień nazwy składniki szablonu:** Kliknij prawym przyciskiem myszy prostokąt w spisie szablonu, zmiana <xref:System.Windows.Shapes.Rectangle> nazwę z "[prostokąt]", "outerRectangle", a następnie zmień element "[ContentPresenter]" na "myContentPresenter".  
  
     ![Jak zmienić nazwę składnika szablonu](./media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3.  **ALTER prostokąt, tak aby był pusty wewnątrz (na przykład pierścieniowy):** Wybierz **outerRectangle** i ustaw <xref:System.Windows.Shapes.Shape.Fill%2A> "Przezroczysty" i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> do 5.  
  
     ![Sposób opróżnić prostokąt](./media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Następnie ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> kolorów niezależnie od rodzaju szablon będzie. Aby to zrobić, kliknij małe pole biały **obrysu**, wybierz opcję **CustomExpression**, a następnie wpisz "{tła TemplateBinding}" w oknie dialogowym.  
  
     ![Jak ustawić stosowanie koloru szablonu](./media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4.  **Utwórz wewnętrzny prostokąt:** Teraz Utwórz inny prostokąt (nadaj mu nazwę "innerRectangle") i umieść ją w symetrycznie wewnątrz **outerRectangle** . Dla tego rodzaju pracy prawdopodobnie można powiększać przycisku większe w obszarze edycji.  
  
    > [!NOTE]
    >  Prostokąt może wyglądać innej niż na ilustracji (na przykład, jego może mieć zaokrąglone rogi).  
  
     ![Jak utworzyć prostokąt wewnątrz innego prostokąta](./media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5.  **Przenieś element ContentPresenter u góry:** W tym momencie jest to możliwe, że tekst "Button" nie będą widoczne dłużej. Jeśli jest to tak, jest to spowodowane **innerRectangle** jest w górnej części **myContentPresenter**. Aby rozwiązać ten problem, przeciągnij **myContentPresenter** poniżej **innerRectangle**. Zmienianie położenia prostokąty i **myContentPresenter** wyglądały podobnie jak na poniższej ilustracji.  
  
    > [!NOTE]
    >  Alternatywnie, możesz także określić położenie **myContentPresenter** u góry, klikając go prawym przyciskiem myszy, a następnie naciskając klawisz **wysyłania do przodu**.  
  
     ![Jak przenieść przycisk na inny przycisk](./media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6.  **Zmiana wyglądu innerRectangle:** Ustaw <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> wartości do 20. In Addition, ustaw <xref:System.Windows.Shapes.Shape.Fill%2A> do tła szablonu przy użyciu wyrażenia niestandardowego "{tła TemplateBinding}") i ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> na "przezroczyste". Należy zauważyć, że ustawienia <xref:System.Windows.Shapes.Shape.Fill%2A> i <xref:System.Windows.Shapes.Shape.Stroke%2A> z **innerRectangle** są przeciwieństwem przypadku **outerRectangle**.  
  
     ![Jak zmienić wygląd prostokąta](./media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7.  **Dodaj warstwę szkła u góry:** Dostosowywanie wyglądu przycisku ostatni element jest dodanie warstwy szkła u góry. Ta warstwa szkła składa się z trzeciej prostokąta. Ponieważ szkła obejmie cały przycisku, prostokąt szkła jest podobna we wymiarów **outerRectangle**. W związku z tym, Utwórz prostokąt, po prostu tworząc kopię **outerRectangle**. Wyróżnij **outerRectangle** i użyj klawiszy CTRL + C i CTRL + V do skopiowania. Nazwij nowy prostokąt "glassCube".  
  
8.  **Jeśli to konieczne, należy zmienić położenie glassCube:** Jeśli **glassCube** jest nie jest jeszcze ustawiony, tak, aby zajmowała cały przycisk, przeciągnij go do określonej pozycji.  
  
9. **Nadaj glassCube kształt nieco inne niż outerRectangle:** Zmiana właściwości **glassCube**. Początek, zmieniając <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości do 10 i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> do 2.  
  
     ![Ustawienia wyglądu glassCube](./media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Wprowadź glassCube wygląda jak szkło:** Ustaw <xref:System.Windows.Shapes.Shape.Fill%2A> glassy wyglądzie przy użyciu gradientu liniowego, wynosi 75% nieprzezroczystych i przełącza między kolor biały i przezroczysty ponad 6 przybliżeniu równomiernie rozmieszczonych odstępach czasu. Jest to, co równa ograniczniki gradientu:  
  
    -   Ogranicznik gradientu 1: Kolor biały z wartości alfa 75%  
  
    -   Ogranicznik gradientu 2: Przezroczyste  
  
    -   Ogranicznik gradientu 3: Kolor biały z wartości alfa 75%  
  
    -   Ogranicznik gradientu 4: Przezroczyste  
  
    -   Ogranicznik gradientu 5: Kolor biały z wartości alfa 75%  
  
    -   Ogranicznik gradientu 6: Przezroczyste  
  
     Spowoduje to utworzenie wygląd szkła "faliste".  
  
     ![Prostokąt, który wygląda jak szkło](./media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Ukryj warstwę szkła:** Teraz, zobaczysz, jak wygląda glassy warstwy, przejdź do **okienko wygląd** z **panelu właściwości** i ustawić nieprzezroczystość 0%, aby je ukryć. W sekcjach wyprzedzeniem użyjemy wyzwalacze właściwości i zdarzeń do wyświetlania i manipulowania warstwy szkła.  
  
     ![Jak ukryć prostokąt szkła](./media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Dostosowywanie zachowania przycisku  
 W tym momencie prezentacji przycisk został dostosowany, edytując jej szablon, ale przycisku nie reaguje na działanie użytkownika jak przyciski typowe (na przykład zmiana wyglądu od wskaźnika myszy nad odbieranie fokus i klikając.) Następne dwa procedury przedstawiają metody do tworzenia zachowań, takie jak te w niestandardowy przycisk. Firma Microsoft będzie rozpoczynać wyzwalacze właściwości prostej, a następnie dodaj wyzwalacze zdarzeń i animacji.  
  
#### <a name="to-set-property-triggers"></a>Aby ustawić wyzwalacze właściwości  
  
1.  **Utwórz nowy wyzwalacz właściwości:** Za pomocą **glassCube** zaznaczone, kliknij przycisk **+ właściwość** w **wyzwalaczy** panelu (patrz rysunek, który następuje po następnym krokiem). Spowoduje to utworzenie wyzwalacz właściwości z domyślny wyzwalacz właściwości.  
  
2.  **Wprowadź IsMouseOver właściwość używana przez wyzwalacz:** Zmień właściwość <xref:System.Windows.UIElement.IsMouseOver%2A>. To sprawia, że wyzwalacz właściwości podczas aktywowania <xref:System.Windows.UIElement.IsMouseOver%2A> właściwość `true` (po użytkownik wskaże przycisk za pomocą myszy).  
  
     ![Jak ustawić wyzwalacz na właściwość](./media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3.  **Nieprzezroczystość wyzwalaczy IsMouseOver 100% glassCube:** Należy zauważyć, że **wyzwalacza — nagrywanie jest włączone** (patrz na poprzednim rysunku). Oznacza to, że wszelkie zmiany wprowadzone do wartości właściwości **glassCube** podczas nagrywania znajduje się w stanie się akcja ma miejsce, gdy <xref:System.Windows.UIElement.IsMouseOver%2A> jest `true`. Podczas nagrywania, zmień <xref:System.Windows.UIElement.Opacity%2A> z **glassCube** do 100%.  
  
     ![Jak ustawić nieprzezroczystość przycisku](./media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     Utworzono pierwszą wyzwalacza właściwości. Należy zauważyć, że **panelu wyzwalaczy** edytora zarejestrował <xref:System.Windows.UIElement.Opacity%2A> zmieniane na 100%.  
  
     ![Panel "Triggers"](./media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Naciśnij klawisz F5, aby uruchomić aplikację, a następnie przesuń wskaźnik myszy nad i wyłączanie przycisku. Powinien zostać wyświetlony warstwy szkła są wyświetlane, gdy przycisk myszą i znikają po odsunięciu wskaźnika.  
  
4.  **Wyzwalacze IsMouseOver obrysu zmiana wartości:** Umożliwia kojarzenie niektóre akcje, za pomocą <xref:System.Windows.UIElement.IsMouseOver%2A> wyzwalacza. Nadal nagrywania, Przełącz zaznaczenie z **glassCube** do **outerRectangle**. Następnie ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> z **outerRectangle** niestandardowe wyrażenie "{dynamicresource — {x: Static SystemColors.HighlightBrushKey}}". To ustawienie <xref:System.Windows.Shapes.Shape.Stroke%2A> na typowej Wyróżnij kolor używany przez przycisków. Naciśnij klawisz F5, aby zobaczyć efekt, gdy wskaźnik myszy nad przyciskiem.  
  
     ![Jak ustawić skok na kolor wyróżnienia](./media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5.  **IsMouseOver wyzwala rozmyty tekst:** Umożliwia kojarzenie jednego więcej akcji <xref:System.Windows.UIElement.IsMouseOver%2A> wyzwalacza właściwości. Oznaczanie zawartości przycisku być nieco rozmyte, gdy szkła pojawi się nad nią. Aby to zrobić, można zastosować Rozmycie <xref:System.Windows.Media.Effects.BitmapEffect> do <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).  
  
     ![Jak rozmycie zawartość przycisku](./media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    >  Aby powrócić **panelu właściwości** do jakich it sprzed czy wyszukiwanie <xref:System.Windows.Media.Effects.BitmapEffect>, wyczyść tekst z **pole wyszukiwania**.  
  
     W tym momencie użyliśmy wyzwalacz właściwości z kilka skojarzonych z nimi działań do utworzenia wyróżnianie zachowania w przypadku, gdy wskaźnik myszy wprowadza i opuszcza obszar przycisku. Inne typowe zachowanie dla przycisku jest Podświetl, gdy ma ona fokus (tak jak po kliknięciu). Możemy dodać zachowanie przez dodanie kolejnego wyzwalacza właściwości dla <xref:System.Windows.UIElement.IsFocused%2A> właściwości.  
  
6.  **Utwórz wyzwalacz właściwości dla IsFocused:** Przy użyciu tej samej procedury jak w przypadku <xref:System.Windows.UIElement.IsMouseOver%2A> (patrz pierwszym krokiem w tej sekcji), utworzenia innego wyzwalacza właściwości dla <xref:System.Windows.UIElement.IsFocused%2A> właściwości. Gdy **wyzwalacza — nagrywanie jest włączone**, Dodaj następujące akcje do wyzwalacza:  
  
    -   **glassCube** pobiera <xref:System.Windows.UIElement.Opacity%2A> 100%.  
  
    -   **outerRectangle** pobiera <xref:System.Windows.Shapes.Shape.Stroke%2A> niestandardowe wyrażenie wartości "{dynamicresource — {x: Static SystemColors.HighlightBrushKey}}".  
  
 Ostatni krok w tym przewodniku dodamy animacji do przycisku. Te animacje będą wyzwalane przez zdarzenia — w szczególności <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Na potrzeby interakcyjności wyzwalacze zdarzeń i animacji  
  
1.  **Tworzenie wyzwalacza zdarzeń MouseEnter:** Dodaj nowy wyzwalacz zdarzenia, a następnie wybierz pozycję <xref:System.Windows.UIElement.MouseEnter> jako zdarzenie do użycia w wyzwalaczu.  
  
     ![Jak utworzyć wyzwalacz zdarzeń MouseEnter](./media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2.  **Utwórz oś czasu animacji:** Następnie należy skojarzyć osi czasu animacji w celu <xref:System.Windows.UIElement.MouseEnter> zdarzeń.  
  
     ![Jak dodać oś czasu animacji do zdarzenia](./media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Po naciśnięciu klawisza **OK** do utworzenia nowego osi czasu, **panelu Oś czasu** pojawia się i "Oś czasu — nagrywanie jest włączone" jest widoczny w okienku projektowania. Oznacza to, że możemy rozpocząć nagrywanie zmiany właściwości (właściwość animowanie zmian) na osi czasu.  
  
    > [!NOTE]
    >  Może być konieczne zmiany rozmiaru okna i/lub paneli, aby wyświetlić ekran.  
  
     ![Panel oś czasu](./media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3.  **Utwórz ramkę kluczową:** Aby utworzyć animację, zaznacz obiekt, który chcesz animować, Utwórz dwa lub więcej ramek kluczowych na osi czasu, a także dla tych ramkami kluczowymi, ustaw wartości właściwości, które mają animacji do interpolacji między. Poniższa ilustracja przeprowadzi Cię przez tworzenie klatki kluczowej.  
  
     ![Jak utworzyć ramkę kluczową](./media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4.  **Zmniejszanie glassCube w tej ramki kluczowej:** Z drugiej klatki kluczowej, zaznaczone, należy zmniejszyć rozmiar **glassCube** do 90% firm z jego za pomocą pełnego rozmiaru **Przekształcanie rozmiar**.  
  
     ![Jak zmniejszyć rozmiar przycisku](./media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Naciśnij klawisz F5, aby uruchomić aplikację. Przesuń wskaźnik myszy nad przyciskiem. Należy zauważyć, że warstwy szkła zmniejsza się na górze przycisku.  
  
5.  **Utwórz kolejny wyzwalacz zdarzenia i skojarzyć inną animację z nią:** Dodajmy jednej więcej animacji. Użyj podobnej procedury używane do utworzenia poprzedniej animacji wyzwalacz zdarzenia:  
  
    1.  Utwórz nowy wyzwalacz zdarzenia, za pomocą <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
    2.  Skojarz nowe osi czasu z <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
     ![Jak utworzyć nową oś czasu](./media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1.  Dla tej osi czasu należy utworzyć dwóch klatki kluczowe — jedną na 0.0 sekund, a drugi na 0,3 sekund.  
  
    2.  Za pomocą ramki kluczowej na 0,3 sekund wyróżniony, ustaw **Obróć kąt Przekształcanie** do 360 stopni.  
  
     ![Jak utworzyć obrót — przekształcenie](./media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1.  Naciśnij klawisz F5, aby uruchomić aplikację. Kliknij przycisk. Należy zauważyć, że warstwy szkła uruchamia się wokół.  
  
## <a name="conclusion"></a>Wniosek  
 Dostosowany przycisk została ukończona. Zrobiono to przy użyciu szablonu przycisku, który został zastosowany do wszystkich przycisków w aplikacji. Jeśli pozostawisz szablonu tryb edycji (patrz poniższy rysunek) i utworzyć więcej przycisków, zostanie wyświetlony wyglądają i zachowują się jak przycisk niestandardowy, a nie jak przycisk domyślny.  
  
 ![Szablon niestandardowy przycisk](./media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![Wiele przycisków, które używają tego samego szablonu](./media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 Naciśnij klawisz F5, aby uruchomić aplikację. Kliknij przyciski i zwróć uwagę, jak one działają tak samo.  
  
 Należy pamiętać, gdy zostały dostosowywania szablonu, ustawienie <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość **innerRectangle** i <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwość **outerRectangle** do tła szablonu ({ TemplateBinding tło}). W związku z tym po ustawieniu Kolor tła przycisków poszczególnych tła, gdy ustawiasz stosowanych w odniesieniu do odpowiednich właściwości. Spróbuj zmienić teraz w tle. Na poniższej ilustracji są używane różne gradienty. W związku z tym mimo że szablon jest przydatne w przypadku dostosowania ogólne formanty, takie jak przycisk, kontrolki z szablonami nadal można modyfikować, aby różnić się od siebie nawzajem.  
  
 ![Przyciski z tego samego szablonu, które wyglądają inaczej](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 Podsumowując w trakcie dostosowywania szablonu przycisku wiesz jak wykonać następujące czynności w programie Microsoft Expression Blend:  
  
-   Dostosowywanie wyglądu formantu.  
  
-   Ustaw wyzwalacze właściwości. Wyzwalacze właściwości są bardzo przydatne, ponieważ mogą być używane w większości obiektów, nie tylko formanty.  
  
-   Ustaw wyzwalacze zdarzeń. Wyzwalacze zdarzeń są bardzo przydatne, ponieważ mogą być używane w większości obiektów, nie tylko formanty.  
  
-   Tworzenie animacji.  
  
-   Różne: Tworzenie gradientów, Dodaj BitmapEffects, użyj przekształceń i ustaw podstawowe właściwości obiektów.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie przycisku przy użyciu języka XAML](walkthrough-create-a-button-by-using-xaml.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Przegląd Animacja](../graphics-multimedia/animation-overview.md)
- [Przegląd Malowanie jednolitymi kolorami i gradientami](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Przegląd Efekty mapy bitowej](../graphics-multimedia/bitmap-effects-overview.md)
