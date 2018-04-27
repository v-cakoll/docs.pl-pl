---
title: 'Wskazówki: utwórz przycisk przy użyciu Microsoft Expression Blend'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e029537466e836cfc103bad64d4102652162c465
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Wskazówki: utwórz przycisk przy użyciu Microsoft Expression Blend
Ten przewodnik zawiera kroki procesu tworzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dostosowany przycisk przy użyciu Microsoft Expression Blend.  
  
> [!IMPORTANT]
>  Microsoft Expression Blend działa przez generowanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] następnie kompilowania dokonanie program wykonywalny. Zamiast czy podczas pracy z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bezpośrednio, istnieje inny wskazówki, tworzącą tej samej aplikacji, jak to użycie jednego [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] z programu Visual Studio, a nie mieszania. Zobacz [utworzyć przycisk przy użyciu języka XAML](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md) Aby uzyskać więcej informacji.  
  
 Na poniższej ilustracji przedstawiono dostosowany przycisk zostanie utworzenie.  
  
 ![Dostosowany przycisk, który spowoduje utworzenie](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Konwertuj kształt do przycisku  
 W pierwszej części tego przewodnika, możesz utworzyć niestandardowy wygląd przycisku niestandardowego. W tym celu należy najpierw Konwertuj prostokąt na przycisku. Można następnie dodać dodatkowe kształty do szablonu po kliknięciu przycisku tworzenia bardziej złożonych przycisk wyglądającej. Dlaczego nie rozpoczynać regularne przycisk i dostosować go? Ponieważ przycisk ma wbudowaną funkcję, która nie ma potrzeby; dla przycisków niestandardowych łatwiej jest rozpoczynać prostokąta.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Aby utworzyć nowy projekt w programie Expression Blend  
  
1.  Uruchom Expression Blend. (Kliknij **Start**, wskaż polecenie **wszystkie programy**, wskaż polecenie **Microsoft Expression**, a następnie kliknij przycisk **Microsoft Expression Blend**.)  
  
2.  Zmaksymalizuj aplikacji, jeśli to konieczne.  
  
3.  Na **pliku** menu, kliknij przycisk **nowy projekt**.  
  
4.  Wybierz **standardowej aplikacji (.exe)**.  
  
5.  Nazwij projekt `CustomButton` i naciśnij klawisz **OK**.  
  
 W tym momencie masz pusty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projektu. Naciśnij klawisz F5, aby uruchomić aplikację. Zgodnie z oczekiwaniami może aplikacja składa się z puste okno. Następnie utwórz zaokrąglony prostokąt i przekonwertować go na przycisku.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Aby przekonwertować prostokąt na przycisku  
  
1.  **Ustaw właściwość okna tła na kolor czarny:** wybierz okno, kliknij przycisk **karta właściwości**i ustaw <xref:System.Windows.Controls.Control.Background%2A> właściwości `Black`.  
  
     ![Jak ustawić tło przycisku na kolor czarny](../../../../docs/framework/wpf/controls/media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2.  **Rysuj prostokąt około rozmiar przycisku w oknie:** wybierz narzędzie Prostokąt na panelu Narzędzia po lewej stronie i przeciągnij prostokąt okna.  
  
     ![Jak narysować prostokąt](../../../../docs/framework/wpf/controls/media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3.  **ROUND limit narożników prostokąta:** przeciągnij punkty kontrolne prostokąta albo bezpośrednio ustawić <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości. Ustaw wartości <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> do 20.  
  
     ![Porady: tworzenie narożników prostokąta Rundy](../../../../docs/framework/wpf/controls/media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4.  **Zmień prostokąta do przycisku:** wybierz prostokąta. Na **narzędzia** menu, kliknij przycisk **upewnij przycisk**.  
  
     ![Porady: tworzenie kształtu do przycisku](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5.  **Określ zakres szablonu/stylu:** tak, zostanie wyświetlone następujące okno dialogowe.  
  
     ![Okno dialogowe "Tworzenia zasobów stylu"](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     Aby uzyskać **Nazwa zasobu (klucza)**, wybierz pozycję **Zastosuj do wszystkich**.  Spowoduje to wynikowy styl i szablon przycisk Zastosuj do wszystkich obiektów, które są przyciski. Aby uzyskać **zdefiniować w**, wybierz pozycję **aplikacji**. Spowoduje to wynikowy styl i przycisk szablonu ma zakresu w całej aplikacji. Po ustawieniu wartości tych dwóch pól styl przycisku i szablonu mają zastosowanie do wszystkich przycisków w całej aplikacji i dowolnego przycisku utworzone w aplikacji domyślnie użyje tego szablonu.  
  
## <a name="edit-the-button-template"></a>Edytuj szablon przycisku  
 Masz teraz prostokąt, który został zmieniony na przycisku. W tej sekcji możesz zmodyfikować szablon przycisku i dostosować, jak wygląda.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Aby edytować szablon przycisk, aby zmienić wygląd przycisku  
  
1.  **Przejdź do widoku edycji szablonu:** dostosować wygląd naszego przycisku, musimy Edytuj szablon przycisku. Ten szablon został utworzony, gdy prostokąt możemy przekonwertować na przycisku. Aby edytować szablon przycisku, kliknij prawym przyciskiem i wybierz **części kontrolki edycji (szablonu)** , a następnie **Edytuj szablon**.  
  
     ![Jak edytować szablon](../../../../docs/framework/wpf/controls/media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     W edytorze szablonu należy zauważyć, że przycisk teraz jest podzielone na <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Controls.ContentPresenter>. <xref:System.Windows.Controls.ContentPresenter> Służy do prezentowania zawartości przycisku (na przykład ciąg "Button"). Zarówno prostokąt i <xref:System.Windows.Controls.ContentPresenter> układ wewnątrz <xref:System.Windows.Controls.Grid>.  
  
     ![Składniki w prezentacji prostokąta](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2.  **Zmiana nazw składniki szablonu:** kliknij prawym przyciskiem myszy prostokąt w spisie szablonu, zmień <xref:System.Windows.Shapes.Rectangle> nazwę z "[prostokąt]" do "outerRectangle" i "myContentPresenter" Zmień "[ContentPresenter]".  
  
     ![Jak zmienić nazwę składnika szablonu](../../../../docs/framework/wpf/controls/media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3.  **Zmienić prostokąta, tak aby nie jest pusty wewnątrz (na przykład pierścień):** wybierz **outerRectangle** i ustaw <xref:System.Windows.Shapes.Shape.Fill%2A> "Transparent" i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> do 5.  
  
     ![Jak opróżnić prostokąt](../../../../docs/framework/wpf/controls/media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Następnie ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> kolorów niezależnie od będzie szablonu. Aby to zrobić, kliknij pole białe małych **obrysu**, wybierz pozycję **CustomExpression**i wpisz w oknie dialogowym "{tła TemplateBinding}".  
  
     ![Jak ustawić stosowanie koloru szablonu](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4.  **Utwórz prostokąt wewnętrznego:** , Utwórz innego prostokąta (nazwę "innerRectangle") i umieść go symetrycznie wewnątrz **outerRectangle** . Dla tego rodzaju pracy prawdopodobnie można powiększać przycisku większe w obszarze edycji.  
  
    > [!NOTE]
    >  Prostokąt może wyglądać inaczej niż na ilustracji (na przykład go może mieć zaokrąglone narożniki).  
  
     ![Jak utworzyć prostokąt wewnątrz innego prostokąta](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5.  **Przenieś na początek ContentPresenter:** w tym momencie jest to możliwe, że tekst "Button" nie będą widoczne dłużej. Jeśli tak, to dlatego **innerRectangle** jest nad **myContentPresenter**. Aby rozwiązać ten problem, przeciągnij **myContentPresenter** poniżej **innerRectangle**. Zmienia położenie prostokąty i **myContentPresenter** do wyglądać podobnie jak poniżej.  
  
    > [!NOTE]
    >  Alternatywnie można również umieścić **myContentPresenter** u góry, klikając go prawym przyciskiem myszy, a następnie naciskając klawisz **wysłać do przodu**.  
  
     ![Jak przenieść przycisk na inny przycisk](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6.  **Zmienianie wyglądu innerRectangle:** ustawić <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> wartości do 20. Ustaw in Addition, <xref:System.Windows.Shapes.Shape.Fill%2A> do tła szablonu przy użyciu wyrażenia niestandardowego "{tła TemplateBinding}") i ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> na "przezroczyste". Zwróć uwagę, że ustawienia <xref:System.Windows.Shapes.Shape.Fill%2A> i <xref:System.Windows.Shapes.Shape.Stroke%2A> z **innerRectangle** są przeciwieństwem dla **outerRectangle**.  
  
     ![Jak zmienić wygląd prostokąta](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7.  **Dodaj warstwę awaryjne na wierzchu:** ostatni element Dostosowywanie wyglądu przycisku jest dodanie warstwy szkła w górnej części. Ta warstwa szkła składa się z trzeci prostokąta. Ponieważ szkła obejmuje całego przycisku, prostokąt szkła przypomina w wymiarach, aby **outerRectangle**. W związku z tym utworzyć prostokąt po prostu wykonując kopię **outerRectangle**. Wyróżnij **outerRectangle** i użyj klawiszy CTRL + C i CTRL + V do skopiowania. Nazwa nowej prostokąta "glassCube".  
  
8.  **Zmienia położenie glassCube, jeśli to konieczne:** Jeśli **glassCube** jest nie jest jeszcze ustawiony tak, aby obejmuje całego przycisku, przeciągnij go do określonej pozycji.  
  
9. **Nadaj glassCube kształt nieco inne niż outerRectangle:** zmiana właściwości **glassCube**. Rozpocząć zmieniając <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości do 10 i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 2.  
  
     ![Ustawienia wyglądu glassCube](../../../../docs/framework/wpf/controls/media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Wprowadź glassCube wyglądać szkła:** ustawić <xref:System.Windows.Shapes.Shape.Fill%2A> glassy wyglądzie przy użyciu gradientu liniowego 75% nieprzezroczystych i przełącza między kolor biały i przezroczysty przez 6 przybliżeniu równomiernie rozłożone odstępach czasu. Jest to, co ma ustawioną wartość gradientu:  
  
    -   Gradientu 1: Białe o wartości alfa 75%  
  
    -   Gradient zatrzymać 2: przezroczyste  
  
    -   Gradientu 3: Białe o wartości alfa 75%  
  
    -   Gradient zatrzymać 4: przezroczyste  
  
    -   Gradientu 5: Białe o wartości alfa 75%  
  
    -   Gradient zatrzymać 6: przezroczyste  
  
     Spowoduje to utworzenie wygląd szkła "faliste".  
  
     ![Prostokąt, który wygląda jak szkła](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Ukryj warstwę szkła:** teraz, zobaczysz, jak wygląda glassy warstwy, przejdź do **okienko wygląd** z **panelu właściwości** i ustaw przezroczystość na % 0, aby je ukryć. W sekcjach wyprzedzeniem użyjemy wyzwalaczy właściwości i zdarzeń do wyświetlania i modyfikowania warstwy awaryjne.  
  
     ![Jak ukryć prostokąt szkła](../../../../docs/framework/wpf/controls/media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Dostosowywanie zachowania przycisku  
 W tym momencie dostosowano prezentacji przycisku, edytując jej szablon, ale przycisku nie reaguje na działanie użytkownika jak przyciski typowe (na przykład zmiana wyglądu po myszą odbieranie fokus i kliknięcie.) Obok dwie procedury pokazują, jak zbudować zachowań, takich jak te w niestandardowych przycisk. Firma Microsoft będzie rozpoczynać się od właściwości prostej wyzwalaczy, a następnie dodaj wyzwalacze zdarzeń i animacji.  
  
#### <a name="to-set-property-triggers"></a>Aby ustawić właściwość wyzwala  
  
1.  **Tworzenie nowego wyzwalacza właściwości:** z **glassCube** zaznaczone, kliknij przycisk **+ właściwości** w **wyzwalaczy** panelu (patrz rysunek, po następnym kroku). Spowoduje to utworzenie wyzwalacza właściwości z poziomu wyzwalacza właściwości domyślnej.  
  
2.  **Wprowadź IsMouseOver właściwość używana przez wyzwalacz:** Zmień właściwość <xref:System.Windows.UIElement.IsMouseOver%2A>. Dzięki temu podczas aktywowania wyzwalacza właściwości <xref:System.Windows.UIElement.IsMouseOver%2A> jest właściwość `true` (gdy użytkownik wskazuje przycisk myszy).  
  
     ![Jak ustawić wyzwalacz we właściwości](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3.  **IsMouseOver wyzwala nieprzezroczystość 100% glassCube:** Zwróć uwagę, że **nagrywanie wyzwalacza jest włączone** (patrz rysunek poprzedniego). Oznacza to, że wszystkie zmiany wprowadzone do wartości właściwości **glassCube** podczas rejestrowania jest w stanie się akcja ma miejsce, gdy <xref:System.Windows.UIElement.IsMouseOver%2A> jest `true`. Podczas nagrywania, zmień <xref:System.Windows.UIElement.Opacity%2A> z **glassCube** 100%.  
  
     ![Jak ustawić nieprzezroczystość przycisku](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     Twój pierwszy wyzwalacz właściwość została utworzona. Zwróć uwagę, że **panelu wyzwalaczy** edytora zarejestrował <xref:System.Windows.UIElement.Opacity%2A> zmieniony na 100%.  
  
     ![Panel "Wyzwalaczy"](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Naciśnij klawisz F5, aby uruchomić aplikację i Przenieś wskaźnik myszy nad i wyłączanie przycisku. Powinny pojawić się warstwy awaryjne są wyświetlane, gdy przycisk myszą i zniknąć po opuszczeniu przez wskaźnik.  
  
4.  **Wyzwalacze IsMouseOver obrysu zmiany wartości:** umożliwia kojarzenie niektóre inne czynności <xref:System.Windows.UIElement.IsMouseOver%2A> wyzwalacza. Podczas rejestrowania będzie nadal występował, Przełącz wybór z **glassCube** do **outerRectangle**. Następnie ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> z **outerRectangle** do niestandardowego wyrażenia "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}". To ustawienie <xref:System.Windows.Shapes.Shape.Stroke%2A> do typowych zaznacz kolor używany przez przycisków. Naciśnij klawisz F5, aby zobaczyć efekt, gdy mysz nad przyciskiem.  
  
     ![Jak ustawić pociągnięcie do koloru wyróżnienia](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5.  **IsMouseOver wyzwala rozmyty tekst:** umożliwia kojarzenie jednego więcej akcji <xref:System.Windows.UIElement.IsMouseOver%2A> wyzwalacza właściwości. Należy zawartości przycisku być nieco rozmyte, gdy szkła pojawi się nad nim. Aby to zrobić, można zastosować rozmycia <xref:System.Windows.Media.Effects.BitmapEffect> do <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).  
  
     ![Jak rozmycia zawartości przycisku](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    >  Aby powrócić **panelu właściwości** do jakie sprzed czy wyszukiwanie <xref:System.Windows.Media.Effects.BitmapEffect>, usuń wartość tekstową z **pole wyszukiwania**.  
  
     W tym momencie użyliśmy wyzwalacza właściwości z kilka skojarzonych z nimi działań do utworzenia wyróżnienia zachowania w przypadku, gdy wskaźnik myszy uzyskuje i opuszcza obszar przycisku. Inne typowe zachowanie dla przycisku jest aby wyróżnić fokus (tak jak po kliknięciu). Takie zachowanie można dodać, dodając inny wyzwalacza właściwości dla <xref:System.Windows.UIElement.IsFocused%2A> właściwości.  
  
6.  **Tworzenie wyzwalacza właściwości dla IsFocused:** przy użyciu tej samej procedury, jak w przypadku <xref:System.Windows.UIElement.IsMouseOver%2A> (zobacz pierwszym krokiem w tej sekcji) i utworzyć inną właściwość wyzwalacza dla <xref:System.Windows.UIElement.IsFocused%2A> właściwości. Gdy **nagrywanie wyzwalacza jest włączone**, Dodaj następujące czynności, aby:  
  
    -   **glassCube** pobiera <xref:System.Windows.UIElement.Opacity%2A> 100%.  
  
    -   **outerRectangle** pobiera <xref:System.Windows.Shapes.Shape.Stroke%2A> wartość wyrażenia niestandardowego "{DynamicResource {x: Static SystemColors.HighlightBrushKey}}".  
  
 Ostatni krok w tym przewodniku dodamy animacji na przycisk. Te animacje będą wyzwalane przez zdarzenia — w szczególności <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Na potrzeby interakcyjności wyzwalacze zdarzeń i animacji  
  
1.  **Tworzenie wyzwalacza zdarzeń MouseEnter:** dodać nowego wyzwalacza zdarzenia i wybierz <xref:System.Windows.UIElement.MouseEnter> jako zdarzeń do użycia w wyzwalaczu.  
  
     ![Jak utworzyć wyzwalacz zdarzeń MouseEnter](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2.  **Utwórz oś czasu animacji:** następnie skojarz oś czasu animacji do <xref:System.Windows.UIElement.MouseEnter> zdarzeń.  
  
     ![Jak dodać oś czasu animacji na zdarzenie](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Po naciśnięciu klawisza **OK** Aby utworzyć nowy harmonogram **panelu Oś czasu** pojawia się i "Nagrywanie jest na osi czasu" jest widoczna w panelu Projekt. Oznacza to, że możemy rozpocząć nagrywanie zmiany właściwości (właściwość animowanie zmian) na osi czasu.  
  
    > [!NOTE]
    >  Może być konieczne zmiany rozmiaru okna i/lub panele, aby wyświetlić ekran.  
  
     ![Panel osi czasu](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3.  **Utwórz kluczową:** Aby utworzyć animacji, wybierz obiekt, którego chcesz animować, Utwórz dwa lub więcej ramek kluczowych na osi czasu, a dla tych kluczowych, ustawiania wartości właściwości ma animacji do interpolowania. Poniższej ilustracji przedstawiono tworzenie kluczową.  
  
     ![Jak utworzyć kluczową](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4.  **Zmniejszanie glassCube w tym klatki kluczowej:** z drugiego klatki kluczowej, zaznaczone, zmniejszyć rozmiar **glassCube** do 90% jego przy użyciu pełnego rozmiaru **przekształcenie rozmiar**.  
  
     ![Jak zmniejszyć rozmiar przycisku](../../../../docs/framework/wpf/controls/media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Naciśnij klawisz F5, aby uruchomić aplikację. Przesuń wskaźnik myszy nad przyciskiem. Należy zauważyć, że warstwa szkła zmniejsza na przycisku.  
  
5.  **Utwórz innego wyzwalacza zdarzenia i skojarzyć z nią innej animacji:** Dodajmy jednej więcej animacji. Użyj podobnej procedury używane do tworzenia poprzedniej animacji wyzwalacza zdarzenia:  
  
    1.  Tworzenie nowego wyzwalacza zdarzenia, przy użyciu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
    2.  Skojarz nowe osi czasu z <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
     ![Jak utworzyć nową oś czasu](../../../../docs/framework/wpf/controls/media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1.  Dla tej osi czasu Utwórz dwie klatek kluczowych, co w sekundach 0.0 i drugi w sekundach 0,3.  
  
    2.  Z klatki kluczowej w sekundach 0,3 wyróżnione, ustaw **Obróć kąt przekształcenie** do 360 stopni.  
  
     ![Jak utworzyć przekształcenie obracania](../../../../docs/framework/wpf/controls/media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1.  Naciśnij klawisz F5, aby uruchomić aplikację. Kliknij przycisk. Należy zauważyć, że warstwa szkła obraca się wokół.  
  
## <a name="conclusion"></a>Wniosek  
 Dostosowany przycisk została ukończona. Jak to przy użyciu szablonu przycisku, która została zastosowana do wszystkich przycisków w aplikacji. Jeśli pozostanie w trybie edycji szablonu (zobacz poniższą ilustrację) i utworzyć więcej przycisków, zobaczysz wyglądać i zachowywać się jak przycisk niestandardowe, a nie jak przycisk domyślny.  
  
 ![Szablon niestandardowy przycisk](../../../../docs/framework/wpf/controls/media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![Wiele przycisków tego samego szablonu](../../../../docs/framework/wpf/controls/media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 Naciśnij klawisz F5, aby uruchomić aplikację. Kliknij przyciski i zwróć uwagę, jak wszystkie zachowują się podobnie.  
  
 Należy pamiętać, gdy zostały Dostosowywanie szablonu, ustawienie <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość **innerRectangle** i <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości **outerRectangle** tło szablonu ({ TemplateBinding tło}). W związku z tym gdy kolor tła przycisków poszczególnych tła, które można ustawić zostanie użyty dla odpowiednich właściwości. Spróbuj zmienić teraz tła. Na poniższej ilustracji są używane różne gradienty. W związku z tym mimo że szablon jest przydatne w przypadku dostosowania ogólnej kontroli, jak przycisk, formantów z szablonami nadal można zmodyfikować, aby różnić się od siebie nawzajem.  
  
 ![Przyciski z tego samego szablonu, który wyglądać inaczej](../../../../docs/framework/wpf/controls/media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 Podsumowując w trakcie dostosowywania szablonu przycisk zapoznaniu wykonać następujące czynności w programie Microsoft Expression Blend:  
  
-   Dostosowywanie wyglądu formantu.  
  
-   Ustaw właściwość wyzwalaczy. Wyzwalacze właściwości są bardzo przydatne, ponieważ można ich używać w większości obiektów, nie tylko formanty.  
  
-   Ustaw wyzwalacze zdarzeń. Wyzwalacze zdarzeń są bardzo przydatne, ponieważ można ich używać w większości obiektów, nie tylko formanty.  
  
-   Tworzenie animacji.  
  
-   Różne: Tworzenie gradientów, Dodaj BitmapEffects, użyć transformacji i ustaw podstawowe właściwości obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie przycisku przy użyciu XAML](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Efekty mapy bitowej — przegląd](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
