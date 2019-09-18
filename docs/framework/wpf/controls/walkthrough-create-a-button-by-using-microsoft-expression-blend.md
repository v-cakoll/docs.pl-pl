---
title: 'Przewodnik: Utwórz przycisk przy użyciu Microsoft Expression Blend'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 497cd520731d9a0c96ed2b7cb35fa9f53ba25245
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053461"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Przewodnik: Utwórz przycisk przy użyciu Microsoft Expression Blend

Ten Instruktaż przeprowadzi Cię przez proces tworzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] niestandardowego przycisku przy użyciu programu Microsoft Expression Blend.

> [!IMPORTANT]
> Program Microsoft Expression Blend działa przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] generowanie, które następnie jest kompilowane, aby utworzyć program wykonywalny. Jeśli wolisz bezpośrednio korzystać z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] programu, istnieje inny przewodnik, który tworzy tę samą aplikację, która korzysta [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] z programu Visual Studio, a nie Blend. Aby uzyskać więcej informacji [, zobacz Tworzenie przycisku przy użyciu języka XAML](walkthrough-create-a-button-by-using-xaml.md) .

Na poniższej ilustracji przedstawiono dostosowany przycisk, który zostanie utworzony.

![Dostosowany przycisk, który zostanie utworzony](./media/custom-button-blend-intro.jpg)

## <a name="convert-a-shape-to-a-button"></a>Konwertowanie kształtu na przycisk

W pierwszej części tego przewodnika utworzysz niestandardowy wygląd przycisku niestandardowego. Aby to zrobić, najpierw przekonwertuj prostokąt na przycisk. Następnie możesz dodać dodatkowe kształty do szablonu przycisku, tworząc bardziej skomplikowany przycisk wyszukiwania. Dlaczego nie zaczyna się od zwykłego przycisku i dostosowuje go? Ponieważ przycisk ma wbudowaną funkcję, która nie jest potrzebna; w przypadku przycisków niestandardowych łatwiej jest zacząć od prostokąta.

### <a name="to-create-a-new-project-in-expression-blend"></a>Aby utworzyć nowy projekt w programie Expression Blend

1. Rozpocznij tworzenie wyrażenia Blend. (Kliknij przycisk **Start**, wskaż pozycję **Wszystkie programy**, wskaż pozycję **Microsoft Expression**, a następnie kliknij pozycję **Microsoft Expression Blend**).

2. W razie konieczności Zmaksymalizuj aplikację.

3. W menu **plik** kliknij pozycję **Nowy projekt**.

4. Wybierz pozycję **aplikacja standardowa (. exe)** .

5. Nazwij projekt `CustomButton` i naciśnij przycisk **OK**.

W tym momencie masz pusty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projekt. Możesz nacisnąć klawisz F5, aby uruchomić aplikację. Zgodnie z oczekiwaniami aplikacja składa się tylko z pustego okna. Następnie utworzysz prostokąt zaokrąglony i przekonwertujesz go na przycisk.

### <a name="to-convert-a-rectangle-to-a-button"></a>Aby skonwertować prostokąt na przycisk

1. **Ustaw właściwość tło okna na czerń:** Zaznacz okno, kliknij **kartę właściwości**, a następnie ustaw <xref:System.Windows.Controls.Control.Background%2A> właściwość na. `Black`

    ![Jak ustawić tło przycisku na czerń](./media/custom-button-blend-changebackground.png)

2. **Rysuj prostokąt w przybliżeniu o rozmiar przycisku w oknie:** Wybierz narzędzie Prostokąt w panelu Narzędzia po lewej stronie i przeciągnij prostokąt do okna.

    ![Jak narysować prostokąt](./media/custom-button-blend-drawrect.png)

3. **Zaokrąglij rogi prostokąta:** Przeciągnij punkty kontrolne prostokąta lub bezpośrednio Ustaw <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> właściwości i. <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> Ustaw wartości <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> na 20.

    ![Jak zaokrąglić rogi prostokąta](./media/custom-button-blend-roundcorners.png)

4. **Zmień prostokąt na przycisk:** Wybierz prostokąt. W menu **Narzędzia** kliknij przycisk **Utwórz**.

    ![Jak utworzyć kształt przycisku](./media/custom-button-blend-makebutton.png)

5. **Określ zakres stylu/szablonu:** Pojawia się okno dialogowe podobne do poniższego.

    ![Okno dialogowe "Tworzenie zasobu stylu"](./media/custom-button-blend-makebutton2.gif)

    W obszarze **nazwa zasobu (klucz)** wybierz pozycję **Zastosuj do wszystkich**.  Dzięki temu styl i szablon przycisku będą miały zastosowanie do wszystkich obiektów, które są przyciskami. W **obszarze Definiuj w**wybierz pozycję **aplikacja**. Dzięki temu styl i szablon przycisku będą miały zakres dla całej aplikacji. Po ustawieniu wartości w tych dwóch polach styl i szablon przycisku mają zastosowanie do wszystkich przycisków w całej aplikacji, a dowolny przycisk utworzony w aplikacji będzie domyślnie używać tego szablonu.

## <a name="edit-the-button-template"></a>Edytuj szablon przycisku

Masz teraz prostokąt, który został zmieniony na przycisk. W tej sekcji zmodyfikujesz szablon przycisku i dowiesz się, jak wygląda.

### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Aby edytować szablon przycisku w celu zmiany wyglądu przycisku

1. **Przejdź do widoku Edytuj szablon:** Aby dodatkowo dostosować wygląd przycisku, musimy edytować szablon przycisku. Ten szablon został utworzony po przekonwertowaniu prostokąta na przycisk. Aby edytować szablon przycisku, kliknij prawym przyciskiem myszy przycisk i wybierz polecenie **Edytuj części formantu (szablon)** , a następnie **Edytuj szablon**.

    ![Jak edytować szablon](./media/custom-button-blend-edittemplate.jpg)

    W edytorze szablonów Zwróć uwagę, że przycisk jest teraz podzielony <xref:System.Windows.Shapes.Rectangle> na <xref:System.Windows.Controls.ContentPresenter>i. <xref:System.Windows.Controls.ContentPresenter> Służy do prezentowania zawartości na przycisku (na przykład ciąg "przycisk"). Oba prostokąty i <xref:System.Windows.Controls.ContentPresenter> są zawarte wewnątrz. <xref:System.Windows.Controls.Grid>

    ![Składniki w prezentacji prostokąta](./media/custom-button-blend-templatepanel.png)

2. **Zmień nazwy składników szablonu:** Kliknij prawym przyciskiem myszy prostokąt w spisie szablonu, Zmień <xref:System.Windows.Shapes.Rectangle> nazwę z "[Rectangle]" na "outerRectangle" i zmień wartość "[ContentPresenter]" na "myContentPresenter".

    ![Jak zmienić nazwę składnika szablonu](./media/custom-button-blend-renamecomponents.png)

3. **Zmień prostokąt tak, aby był pusty wewnątrz (na przykład pierścień):** Wybierz pozycję **outerRectangle** , <xref:System.Windows.Shapes.Shape.Fill%2A> a następnie ustaw wartość " <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> transparent" i pozycję 5.

    ![Jak utworzyć prostokąt pusty](./media/custom-button-blend-changerectproperties.png)

    Następnie ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> wartość na kolor niezależnie od tego, jaki będzie szablon. Aby to zrobić, kliknij małe białe pole obok pozycji **pociągnięcia**, wybierz pozycję **CustomExpression**i wpisz "{TemplateBinding background}" w oknie dialogowym.

    ![Jak ustawić kolor szablonu za pomocą](./media/custom-button-blend-templatestroke.png)

4. **Utwórz wewnętrzny prostokąt:** Teraz utwórz kolejny prostokąt (nadaj mu nazwę "innerRectangle") i umieść go symetrycznie w obrębie elementu **outerRectangle** . W przypadku tego rodzaju pracy prawdopodobnie chcesz zwiększyć powiększenie przycisku w obszarze edycji.

    > [!NOTE]
    > Prostokąt może wyglądać inaczej niż jeden na rysunku (na przykład może mieć Zaokrąglone rogi).

    ![Jak utworzyć prostokąt wewnątrz innego prostokąta](./media/custom-button-blend-innerrectangleproperties.png)

5. **Przenieś ContentPresenter na początek:** W tym momencie jest możliwe, że tekst "przycisk" nie będzie dłużej widoczny. W takim przypadku jest to spowodowane tym, że **innerRectangle** znajduje się na szczycie **myContentPresenter**. Aby rozwiązać ten problem, przeciągnij **myContentPresenter** poniżej **innerRectangle**. Zmień położenie prostokątów i **myContentPresenter** , aby wyglądać podobnie do poniższego.

    > [!NOTE]
    > Alternatywnie można również ustawić pozycję **myContentPresenter** w górnej części, klikając ją prawym przyciskiem myszy i naciskając pozycję **Wyślij do przodu**.

    ![Jak przenieść jeden przycisk na inny przycisk](./media/custom-button-blend-innerrectangle2.png)

6. **Zmień wygląd innerRectangle:** Ustaw wartości <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> i<xref:System.Windows.Shapes.Shape.StrokeThickness%2A> na 20. Ponadto ustaw <xref:System.Windows.Shapes.Shape.Fill%2A> wartość na tło szablonu przy użyciu wyrażenia niestandardowego "{TemplateBinding background}") i ustaw wartość <xref:System.Windows.Shapes.Shape.Stroke%2A> "transparent". Zwróć uwagę, że ustawienia dla <xref:System.Windows.Shapes.Shape.Fill%2A> i <xref:System.Windows.Shapes.Shape.Stroke%2A> **innerRectangle** są przeciwieństwem do wartości **outerRectangle**.

    ![Jak zmienić wygląd prostokąta](./media/custom-button-blend-glassrectangleproperties1.png)

7. **Dodaj warstwę szklaną na górze:** Ostateczną częścią dostosowywania wyglądu przycisku jest dodanie warstwy szklanej na górze. Ta warstwa szklana składa się z trzeciego prostokąta. Ponieważ szkło będzie obejmować cały przycisk, prostokąt szklany jest podobny w wymiarach do **outerRectangle**. W związku z tym Utwórz prostokąt, tworząc kopię **outerRectangle**. Podświetl pozycję **outerRectangle** i naciśnij klawisze CTRL + C i Ctrl + V, aby utworzyć kopię. Nazwij ten nowy prostokąt "glassCube".

8. **W razie potrzeby zmień pozycję glassCube:** Jeśli **glassCube** nie jest jeszcze ustawiony, tak aby obejmował cały przycisk, przeciągnij go do pozycji.

9. **Nadaj glassCube nieco inny kształt niż outerRectangle:** Zmień właściwości **glassCube**. Zacznij od zmiany <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> właściwości i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> na wartość <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 10 oraz do 2.

    ![Ustawienia wyglądu dla glassCube](./media/custom-button-blend-glasscubeappearance.gif)

10. **GlassCube wyglądać jak szkło:** <xref:System.Windows.Shapes.Shape.Fill%2A> Ustaw do szklanego wyglądu, używając gradientu liniowego, który jest 75% nieprzezroczysty i alternatywny między kolorem biały i przezroczysty ponad 6 około odstępu. To ustawienie powoduje zatrzymanie gradientu:

    - Stopka gradientu 1: Biały z wartością alfa 75%

    - Stopka gradientu 2: Przezroczyste

    - Stop gradientu 3: Biały z wartością alfa 75%

    - Stopka gradientu 4: Przezroczyste

    - Stopień gradientu 5: Biały z wartością alfa 75%

    - Stopień gradientu 6: Przezroczyste

    Spowoduje to utworzenie "falistej" szyby.

    ![Prostokąt, który wygląda jak szkło](./media/custom-button-blend-glassrectangleproperties2.png)

11. **Ukryj warstwę szklaną:** Teraz, gdy zobaczysz, jak wygląda warstwa szklana, przejdź do **okienka wygląd** **panelu Właściwości** i ustaw krycie na 0%, aby je ukryć. W kolejnych sekcjach będziemy używać wyzwalaczy właściwości i zdarzeń do wyświetlania i manipulowania warstwą szklaną.

    ![Jak ukryć prostokąt szklany](./media/custom-button-glassrectangleproperties3.gif)

## <a name="customize-the-button-behavior"></a>Dostosuj zachowanie przycisku

W tym momencie dostosowano prezentację przycisku przez edycję jego szablonu, ale przycisk nie reaguje na akcje użytkownika jako typowe przyciski (na przykład zmiana wyglądu po przeniesieniu kursora myszy, odebranie fokusu i kliknięcie). W następnych dwóch procedurach pokazano, jak tworzyć zachowania takie jak w przypadku przycisku niestandardowego. Zaczniemy od prostych wyzwalaczy właściwości, a następnie dodawać wyzwalacze i animacje zdarzeń.

### <a name="to-set-property-triggers"></a>Aby ustawić wyzwalacze właściwości

1. **Utwórz nowy wyzwalacz właściwości:** Po wybraniu **glassCube** kliknij pozycję **+ Właściwość** w panelu **wyzwalacze** (zobacz rysunek, który następuje po następnym kroku). Spowoduje to utworzenie wyzwalacza właściwości z domyślnym wyzwalaczem właściwości.

2. **Ustaw IsMouseOver właściwości używanej przez wyzwalacz:** Zmień wartość właściwości na <xref:System.Windows.UIElement.IsMouseOver%2A>. Dzięki temu wyzwalacz właściwości jest uaktywniany, <xref:System.Windows.UIElement.IsMouseOver%2A> gdy właściwość `true` jest (gdy użytkownik wskaże przycisk myszą).

    ![Jak ustawić wyzwalacz dla właściwości](./media/custom-button-blend-ismousedoverpropertytrigger.png)

3. **Nieprzezroczystość wyzwalaczy IsMouseOver 100% dla glassCube:** Zauważ, że **Rejestrowanie wyzwalacza jest włączone** (zobacz poprzedni rysunek). Oznacza to, że wszelkie zmiany wprowadzane do wartości właściwości **glassCube** , gdy nagrywanie jest włączone, staną się akcją, która ma miejsce <xref:System.Windows.UIElement.IsMouseOver%2A> , `true`gdy jest. Podczas rejestrowania Zmień wartość <xref:System.Windows.UIElement.Opacity%2A> z **glassCube** na 100%.

    ![Jak ustawić nieprzezroczystość przycisku](./media/custom-button-blend-ismousedoverpropertytrigger2.gif)

    Teraz został utworzony pierwszy wyzwalacz właściwości. Zauważ, że **panel wyzwalacze** edytora zarejestrował <xref:System.Windows.UIElement.Opacity%2A> zmianę na 100%.

    ![Panel wyzwalacze](./media/custom-button-blend-propertytriggerinfo.png)

    Naciśnij klawisz F5, aby uruchomić aplikację, a następnie przesuń wskaźnik myszy nad przycisk. Po umieszczeniu wskaźnika myszy nad przyciskiem zostanie wyświetlona warstwa szklana, gdy zostanie on wysunięty.

4. **IsMouseOver:** Skojarzmy z <xref:System.Windows.UIElement.IsMouseOver%2A> wyzwalaczem inne akcje. Gdy nagrywanie jest kontynuowane, przełącz wybór z **glassCube** na **outerRectangle**. Następnie ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> wartość elementu **outerRectangle** na wyrażenie niestandardowe "{DynamicResource — {x:static — SystemColors. HighlightBrushKey}}". Ustawia <xref:System.Windows.Shapes.Shape.Stroke%2A> to na typowy kolor wyróżnienia używany przez przyciski. Naciśnij klawisz F5, aby zobaczyć efekt po umieszczeniu wskaźnika myszy nad przyciskiem.

    ![Jak ustawić pociągnięcie do koloru wyróżnienia](./media/custom-button-blend-ismousedoverpropertytrigger3.png)

5. **IsMouseOver wyzwolenie tekstu:** Skojarzmy jeszcze jedną akcję z <xref:System.Windows.UIElement.IsMouseOver%2A> wyzwalaczem właściwości. Wyświetlona zostanie nieznacznie zamazana zawartość przycisku, gdy pojawi się nad nim szkło. W tym celu możemy zastosować rozmycie <xref:System.Windows.Media.Effects.BitmapEffect> <xref:System.Windows.Controls.ContentPresenter> do (**myContentPresenter**).

    ![Jak rozmycie zawartości przycisku](./media/custom-button-blend-propertytriggerwithbitmapeffect.png)

    > [!NOTE]
    > Aby przywrócić **Panel właściwości** z powrotem do tego <xref:System.Windows.Media.Effects.BitmapEffect>, co było przed rozpoczęciem wyszukiwania, wyczyść tekst w **polu wyszukiwania**.

    W tym momencie użyto wyzwalacza właściwości z kilkoma skojarzonymi akcjami, aby utworzyć zachowanie wyróżnienia dla momentu, gdy wskaźnik myszy zostanie wprowadzony i opuści obszar przycisku. Innym typowym zachowaniem przycisku jest wyróżnienie, gdy ma fokus (po kliknięciu). Można dodać takie zachowanie przez dodanie innego wyzwalacza właściwości dla <xref:System.Windows.UIElement.IsFocused%2A> właściwości.

6. **Utwórz wyzwalacz właściwości dla elementu isfocusd:** Korzystając z tej samej procedury jak <xref:System.Windows.UIElement.IsMouseOver%2A> w przypadku (Zobacz pierwszy krok tej sekcji), utwórz kolejny wyzwalacz właściwości <xref:System.Windows.UIElement.IsFocused%2A> dla właściwości. Podczas **rejestrowania wyzwalania**należy dodać następujące akcje do wyzwalacza:

    - **glassCube** pobiera <xref:System.Windows.UIElement.Opacity%2A> 100%.

    - **outerRectangle** pobiera <xref:System.Windows.Shapes.Shape.Stroke%2A> wartość wyrażenia niestandardowego "{DynamicResource — {x:static — SystemColors. HighlightBrushKey}}".

Ostatnim krokiem w tym instruktażu jest dodanie animacji do przycisku. Te animacje będą wyzwalane przez zdarzenia — w tym <xref:System.Windows.UIElement.MouseEnter> zdarzenia i. <xref:System.Windows.Controls.Primitives.ButtonBase.Click>

### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Aby dodać interaktywność przy użyciu wyzwalaczy zdarzeń i animacji

1. **Utwórz wyzwalacz zdarzenia MouseEnter:** Dodaj nowy wyzwalacz zdarzenia i wybierz <xref:System.Windows.UIElement.MouseEnter> jako zdarzenie, które ma być używane w wyzwalaczu.

     ![Jak utworzyć wyzwalacz zdarzenia MouseEnter](./media/custom-button-blend-mouseovereventtrigger.png)

2. **Utwórz oś czasu animacji:** Następnie skojarz oś czasu animacji ze <xref:System.Windows.UIElement.MouseEnter> zdarzeniem.

    ![Jak dodać oś czasu animacji do zdarzenia](./media/custom-button-blend-mouseovereventtrigger2.png)

    Po naciśnięciu przycisku **OK** w celu utworzenia nowej osi czasu zostanie wyświetlony **panel oś czasu** , a opcja "Nagrywanie osi czasu jest włączona" w panelu projektowania. Oznacza to, że można rozpocząć rejestrowanie zmian właściwości na osi czasu (animowane zmiany właściwości).

    > [!NOTE]
    > Może zajść potrzeba zmiany rozmiaru okna i/lub paneli, aby wyświetlić ekran.

    ![Panel oś czasu](./media/custom-button-blend-mouseovereventtrigger3.png)

3. **Utwórz klatkę kluczową:** Aby utworzyć animację, wybierz obiekt, który chcesz animować, Utwórz co najmniej dwa klatki kluczowe na osi czasu, a dla tych klatek kluczowych Ustaw wartości właściwości, które mają być interpolowane dla animacji. Poniższy rysunek przeprowadzi Cię przez proces tworzenia klatki kluczowej.

    ![Jak utworzyć ramkę kluczową](./media/custom-button-blend-mouseovereventtrigger4.png)

4. **Zmniejsz glassCube w tej klatce kluczowej:** Po wybraniu drugiej klatki kluczowej Zmniejsz rozmiar **glassCube** do 90% całkowitego rozmiaru przy użyciu **przekształcenia rozmiaru**.

    ![Jak zmniejszyć rozmiar przycisku](./media/custom-button-blend-sizetransform.png)

    Naciśnij klawisz F5, aby uruchomić aplikację. Przesuń wskaźnik myszy nad przycisk. Zauważ, że warstwa szklana zmniejsza się w górnej części przycisku.

5. **Utwórz inny wyzwalacz zdarzenia i skojarz z nim inną animację:** Dodajmy jeszcze jedną animację. Użyj podobnej procedury do tworzenia poprzedniej animacji wyzwalacza zdarzeń:

    1. Utwórz nowy wyzwalacz zdarzeń przy użyciu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

    2. Skojarz nową oś czasu ze <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeniem.

        ![Jak utworzyć nową oś czasu](./media/custom-button-blend-clickeventtrigger1.png)

    3. Dla tej osi czasu Utwórz dwa klatki kluczowe, jeden o godzinie 0,0 sekund, a drugi na 0,3 sekund.

    4. Gdy klatka kluczowa o 0,3 sekund zostanie wyróżniona, ustaw **kąt przekształcenia Obróć** na 360 stopni.

        ![Jak utworzyć transformację rotacji](./media/custom-button-blend-rotatetransform.gif)

    5. Naciśnij klawisz F5, aby uruchomić aplikację. Kliknij przycisk. Zwróć uwagę, że warstwa szklana obraca się wokół siebie.

## <a name="conclusion"></a>Wniosek

Ukończono dostosowany przycisk. Zostało to wykonane przy użyciu szablonu przycisku, który został zastosowany do wszystkich przycisków w aplikacji. Jeśli opuścisz tryb edycji szablonu (patrz poniższy rysunek) i utworzysz więcej przycisków, zobaczysz, że wyglądają i zachowują się jak przycisk niestandardowy, a nie jako przycisk domyślny.

![Szablon przycisku niestandardowego](./media/custom-button-blend-scopeup.gif)

![Wiele przycisków, które używają tego samego szablonu](./media/custom-button-blend-createmultiplebuttons.png)

Naciśnij klawisz F5, aby uruchomić aplikację. Klikaj przyciski i Zauważ, że wszystkie działają tak samo.

Pamiętaj, że <xref:System.Windows.Shapes.Shape.Fill%2A> podczas dostosowywania szablonu ustawiasz Właściwość <xref:System.Windows.Shapes.Shape.Stroke%2A> innerRectangle oraz Właściwość **outerRectangle** na tło szablonu ({TemplateBinding Background}). W związku z tym po ustawieniu koloru tła poszczególnych przycisków ustawione tło będzie używane dla odpowiednich właściwości. Wypróbuj teraz zmianę tła. Na poniższej ilustracji są używane różne gradienty. W związku z tym mimo że szablon jest przydatny do ogólnego dostosowywania formantów, takich jak Button, nadal można modyfikować kontrolki z szablonami, aby wyglądać inaczej.

![Przyciski z tym samym szablonem, który wyglądu DIFERENT](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")

W ramach procesu dostosowywania szablonu przycisku zawarto informacje na temat wykonywania następujących czynności w programie Microsoft Expression Blend:

- Dostosowywanie wyglądu kontrolki.

- Ustaw wyzwalacze właściwości. Wyzwalacze właściwości są bardzo przydatne, ponieważ mogą być używane w większości obiektów, a nie tylko w kontrolkach.

- Ustaw wyzwalacze zdarzeń. Wyzwalacze zdarzeń są bardzo przydatne, ponieważ mogą być używane w większości obiektów, a nie tylko w kontrolkach.

- Utwórz animacje.

- Różne: Tworzenie gradientów, Dodawanie BitmapEffects, używanie transformacji i Ustawianie podstawowych właściwości obiektów.

## <a name="see-also"></a>Zobacz także

- [Tworzenie przycisku przy użyciu XAML](walkthrough-create-a-button-by-using-xaml.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Animacja — przegląd](../graphics-multimedia/animation-overview.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Efekty mapy bitowej — przegląd](../graphics-multimedia/bitmap-effects-overview.md)
