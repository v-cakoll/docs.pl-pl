---
title: ToolStrip — Architektura formantu
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: e02b9daa40a5f8a2f8bfd8874d006550628a70b3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654725"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip — Architektura formantu
<xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripItem> klasy zapewniają elastyczny i rozszerzalny system do wyświetlania elementów paska narzędzi, stanu i menu. Te klasy są zawarte w <xref:System.Windows.Forms> przestrzeni nazw i ich wszystkie nazwy z prefiksem "ToolStrip" (takie jak <xref:System.Windows.Forms.ToolStripOverflow>) lub z sufiksem "Usuń" (takie jak <xref:System.Windows.Forms.MenuStrip>).  
  
## <a name="toolstrip"></a>ToolStrip  
 W poniższych tematach opisano <xref:System.Windows.Forms.ToolStrip> i kontrolek, które wynikają z niego.  
  
 <xref:System.Windows.Forms.ToolStrip> jest abstrakcyjna klasa bazowa dla <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, i <xref:System.Windows.Forms.ContextMenuStrip>. Następujący obiekt modelu pokazuje <xref:System.Windows.Forms.ToolStrip> hierarchii dziedziczenia.  
  
 ![Diagram przedstawiający ToolStrip modelu obiektów.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)  
  
 Możesz uzyskać dostęp wszystkie elementy w <xref:System.Windows.Forms.ToolStrip> za pośrednictwem <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekcji. Możesz uzyskać dostęp wszystkie elementy w <xref:System.Windows.Forms.ToolStripDropDownItem> za pośrednictwem <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> kolekcji. W klasie pochodnej od <xref:System.Windows.Forms.ToolStrip>, można również użyć <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> właściwość, aby uzyskać dostęp tylko te elementy, które są obecnie wyświetlane. Są to elementy, które nie znajdują się w menu przepełnienia.  
  
 Następujące elementy są specjalnie z myślą o bezproblemowej współpracy z obu <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> w wszystkie orientacje. Są one domyślnie dostępne w czasie projektowania dla <xref:System.Windows.Forms.ToolStrip> sterowania:  
  
- <xref:System.Windows.Forms.ToolStripButton>  
  
- <xref:System.Windows.Forms.ToolStripSeparator>  
  
- <xref:System.Windows.Forms.ToolStripLabel>  
  
- <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
- <xref:System.Windows.Forms.ToolStripSplitButton>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> jest kontenerem najwyższego poziomu, która zastępuje <xref:System.Windows.Forms.MainMenu>. Zapewnia również wiele dokumentów i obsługi kluczowych funkcji interfejsu (MDI). Funkcjonalnie <xref:System.Windows.Forms.ToolStripDropDownItem> i <xref:System.Windows.Forms.ToolStripMenuItem> pracy wraz z <xref:System.Windows.Forms.MenuStrip>, mimo że pochodzą one od <xref:System.Windows.Forms.ToolStripItem>.  
  
 Następujące elementy są specjalnie z myślą o bezproblemowej współpracy z obu <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> w wszystkie orientacje. Są one domyślnie dostępne w czasie projektowania dla <xref:System.Windows.Forms.MenuStrip> sterowania:  
  
- <xref:System.Windows.Forms.ToolStripMenuItem>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> zastępuje <xref:System.Windows.Forms.StatusBar> kontroli. Specjalne funkcje <xref:System.Windows.Forms.StatusStrip> obejmują układu tabeli niestandardowej, pomoc techniczna dotycząca zmiany rozmiaru i przenoszenie grips, formularza i `Spring` właściwość, która umożliwia <xref:System.Windows.Forms.ToolStripStatusLabel> do automatycznego wypełnienia dostępnego miejsca.  
  
 Następujące elementy są specjalnie z myślą o bezproblemowej współpracy z obu <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> w wszystkie orientacje. Są one domyślnie dostępne w czasie projektowania dla <xref:System.Windows.Forms.StatusStrip> sterowania:  
  
- <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
- <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
- <xref:System.Windows.Forms.ToolStripSplitButton>  
  
- <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> zastępuje <xref:System.Windows.Forms.ContextMenu>. Możesz skojarzyć <xref:System.Windows.Forms.ContextMenuStrip> z dowolną kontrolkę, a następnie prawym przyciskiem myszy kliknij automatycznie wyświetla menu kontekstowe (lub menu skrótów). Możesz wyświetlić <xref:System.Windows.Forms.ContextMenuStrip> programowo przy użyciu <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> metody. <xref:System.Windows.Forms.ContextMenuStrip> obsługuje cancelable <xref:System.Windows.Forms.ToolStripDropDown.Opening> i <xref:System.Windows.Forms.ToolStripDropDown.Closing> zdarzeń w celu obsługi dynamicznej populacji i kliknięciem dla wielu scenariuszy. <xref:System.Windows.Forms.ContextMenuStrip> obsługuje obrazy, stan zaznaczenia elementu menu, tekst, klucze dostępu, skróty i kaskadowych menu.  
  
 Następujące elementy są specjalnie z myślą o bezproblemowej współpracy z obu <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> w wszystkie orientacje. Są one domyślnie dostępne w czasie projektowania dla <xref:System.Windows.Forms.ContextMenuStrip> sterowania:  
  
- <xref:System.Windows.Forms.ToolStripMenuItem>  
  
- <xref:System.Windows.Forms.ToolStripSeparator>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>Funkcje ogólne ToolStrip  
 W poniższych tematach opisano funkcje i zachowania, które są ogólnego na <xref:System.Windows.Forms.ToolStrip> i formanty pochodne.  
  
#### <a name="painting"></a>Malowanie  
 Malowanie niestandardowe można zrobić w <xref:System.Windows.Forms.ToolStrip> formantów na kilka sposobów. Podobnie jak w przypadku innych kontrolek Windows Forms <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripItem> mają możliwym do zastąpienia `OnPaint` metod i `Paint` zdarzenia. Zgodnie z regularnych malowania w układzie współrzędnych są określane względem obszaru klienckiego kontrolki; oznacza to, w lewym górnym rogu formantu jest 0, 0. `Paint` Zdarzeń i `OnPaint` metodę <xref:System.Windows.Forms.ToolStripItem> zachowują się jak inne zdarzenia malowania kontroli.  
  
 <xref:System.Windows.Forms.ToolStrip> Kontrolki również zapewnić bardziej precyzyjną dostęp do renderowania elementów i kontener za pośrednictwem <xref:System.Windows.Forms.ToolStripRenderer> klasy, która ma możliwym do zastąpienia metody malowanie tła, tło elementu, obraz elementu, element strzałki, tekst elementu, a obramowania <xref:System.Windows.Forms.ToolStrip>. Argumenty zdarzenia dla tych metod uwidocznić kilka właściwości, takich jak prostokąty, kolory i formatów tekstu, które można dostosować zgodnie z potrzebami.  
  
 Aby dostosować kilka aspektów jak jest malowany element, zazwyczaj zastąpienie <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Jeśli piszesz nowy element, aby kontrolowanie wszystkich aspektów malowanie zastąpić `OnPaint` metody. Z poziomu `OnPaint`, możesz użyć metody z <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Domyślnie <xref:System.Windows.Forms.ToolStrip> to double buforowane, korzystając z zalet <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> ustawienie.  
  
#### <a name="parenting"></a>Elementy nadrzędne  
 Koncepcja kontenerów, własności i element nadrzędny jest bardziej złożone, w <xref:System.Windows.Forms.ToolStrip> kontrolki niż w innych formantów kontenerów Windows Forms. Który jest niezbędny do obsługi dynamicznej scenariuszy, takich jak przepełnienia, udostępniania elementów listy rozwijanej w wielu <xref:System.Windows.Forms.ToolStrip> elementy i obsługuje generowania <xref:System.Windows.Forms.ContextMenuStrip> w kontrolce.  
  
 Poniższa lista zawiera opis elementów członkowskich, powiązany element nadrzędny i opisano ich użycie.  
  
- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> uzyskuje dostęp do elementu, który jest źródłem elementu listy rozwijanej. Jest to podobne do <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, ale zamiast zwracać kontrolki, zwraca <xref:System.Windows.Forms.ToolStripItem>.  
  
- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> Określa, które określają, jest źródłem programu <xref:System.Windows.Forms.ContextMenuStrip> kiedy wiele formantów współużytkować ten sam <xref:System.Windows.Forms.ContextMenuStrip>.  
  
- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> jest tylko do odczytu akcesora do <xref:System.Windows.Forms.ToolStripItem.Parent%2A> właściwości. Element nadrzędny różni się od właściciela, w tym, że element nadrzędny oznacza zwrócone bieżącego <xref:System.Windows.Forms.ToolStrip> , w której element jest wyświetlany, który może być w obszarze przepełnienia.  
  
- <xref:System.Windows.Forms.ToolStripItem.Owner%2A> Zwraca <xref:System.Windows.Forms.ToolStrip> kolekcji elementów, których zawiera bieżącą <xref:System.Windows.Forms.ToolStripItem>. To jest najlepszym sposobem, aby odwołać się do <xref:System.Windows.Forms.ToolStrip.ImageList%2A> lub innych właściwości w najwyższego poziomu <xref:System.Windows.Forms.ToolStrip> bez konieczności pisania kodu specjalne, aby obsłużyć przepełnienia.  
  
#### <a name="behavior-of-inherited-controls"></a>Zachowanie dziedziczonego formantów  
 Następujące elementy sterujące są zablokowane w każdym przypadku, gdy są one używane w dziedziczeniu:  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
- <xref:System.Windows.Forms.MenuStrip>  
  
- <xref:System.Windows.Forms.ContextMenuStrip>  
  
- <xref:System.Windows.Forms.StatusStrip>  
  
- <xref:System.Windows.Forms.ToolStripPanel> zawierającej paneli w <xref:System.Windows.Forms.ToolStripContainer> i również indywidualnych <xref:System.Windows.Forms.ToolStripPanel> kontrolki.  
  
 Na przykład można utworzyć nowej aplikacji Windows Forms przy użyciu co najmniej jedna z kontrolek na poprzedniej liście. Modyfikator dostępu dla formantów, aby ustawić `public` lub `protected`, a następnie Skompiluj projekt. Dodaj formularz, który dziedziczy z pierwszego formularza, a następnie wybierz kontrolkę, która jest dziedziczone. Ten formant jest widoczny zablokowane, zachowuje się tak, jakby był jej modyfikator dostępu `private`.  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer — Obsługa dziedziczenia  
 <xref:System.Windows.Forms.ToolStripContainer> Kontrolka obsługuje ograniczonej liczbie scenariuszy dziedziczone, podobny do poniższego przykładu:  
  
1. Tworzenie nowej aplikacji Windows Forms.  
  
2. Dodaj <xref:System.Windows.Forms.ToolStripContainer> do formularza.  
  
3. Ustaw modyfikator dostępu elementu <xref:System.Windows.Forms.ToolStripContainer> do `public` lub `protected`.  
  
4. Dodaj dowolną kombinację <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.ContextMenuStrip> mające na celu <xref:System.Windows.Forms.ToolStripPanel> regionów <xref:System.Windows.Forms.ToolStripContainer>.  
  
5. Skompiluj projekt.  
  
6. Dodaj formularz, który dziedziczy z pierwszego formularza.  
  
7. Wybierz dziedziczonego <xref:System.Windows.Forms.ToolStripContainer> w formularzu.  
  
#### <a name="inherited-behavior-of-child-controls"></a>Zachowanie dziedziczonego formantów podrzędnych  
 Po wykonaniu poprzednich kroków spowoduje następujące dziedziczone zachowanie:  
  
- W Projektancie kontrolki jest wyświetlana ikona dziedziczone.  
  
- <xref:System.Windows.Forms.ToolStripPanel> Kontrolki są zablokowane; nie można wybrać lub rozmieszczanie ich zawartości.  
  
- Można dodać kontrolki ułatwiające <xref:System.Windows.Forms.ToolStripContentPanel>, Przenieś kontrolki i nadawać im formantów podrzędnych <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
- Zmiany zostaną zachowane po utworzeniu formularza.  
  
    > [!NOTE]
    >  Usuń modyfikatory dostępu ze wszystkich <xref:System.Windows.Forms.ToolStripPanel> formantów, które są częścią <xref:System.Windows.Forms.ToolStripContainer>. Modyfikator dostępu elementu <xref:System.Windows.Forms.ToolStripContainer> kontroluje cały kontroli.  
  
#### <a name="partial-trust"></a>Zaufanie częściowe  
 Ograniczenia `ToolStrip`s w częściowej relacji zaufania mają na celu zapobieganie niepotrzebnemu wpis danych osobowych, które mogą być używane przez osoby nieupoważnione lub usługi. Środków ochronnych są następujące:  
  
- `ToolStripDropDown` Formanty wymagają <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> do wyświetlania elementów w <xref:System.Windows.Forms.ToolStripControlHost>. Dotyczy to zarówno wewnętrzne formantów takich jak <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, i <xref:System.Windows.Forms.ToolStripProgressBar> jako również, aby utworzyć użytkownika decyduje. Jeśli to wymaganie nie jest spełniony, te elementy nie są wyświetlane. Jest zgłaszany żaden wyjątek.  
  
- Ustawienie <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> właściwości `false` nie jest dozwolona oraz można anulować <xref:System.Windows.Forms.ToolStripDropDown.Closing> zdarzenia parametr jest ignorowany. Dzięki temu można wprowadzić więcej niż jednym naciśnięciem klawisza bez odrzuceniu elementu listy rozwijanej. Jeśli to wymaganie nie jest spełniony, nie są wyświetlane takie elementy. Jest zgłaszany żaden wyjątek.  
  
- Wiele naciśnięcia klawisza, obsługa zdarzeń nie zostanie wygenerowany, jeśli występują one w częściowej relacji zaufania kontekstów innych niż <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.  
  
- Klucze dostępu nie są przetwarzane, gdy <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> nie zostało udzielone.  
  
#### <a name="usage"></a>Użycie  
 Następujące wzorce użycia mają wpływ na <xref:System.Windows.Forms.ToolStrip> układ, interakcji klawiatury i zachowanie użytkownika końcowego:  
  
- Przyłączone w <xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip> Może być przeniesiony w ramach <xref:System.Windows.Forms.ToolStripPanel> i na <xref:System.Windows.Forms.ToolStripPanel>s. `Dock` Właściwość jest ignorowana Jeśli <xref:System.Windows.Forms.ToolStrip.Stretch%2A> właściwość `false`, rozmiar <xref:System.Windows.Forms.ToolStrip> rośnie, ponieważ elementy są dodawane do <xref:System.Windows.Forms.ToolStripPanel>. Zazwyczaj <xref:System.Windows.Forms.ToolStrip> nie uczestniczy w kolejności tabulacji.  
  
- Zadokowane  
  
     <xref:System.Windows.Forms.ToolStrip> Znajduje się na jednej stronie kontenera w stałej pozycji i rozmiaru rozszerza się na cały krawędzi, do której jest zadokowany. Zazwyczaj <xref:System.Windows.Forms.ToolStrip> nie uczestniczy w kolejności tabulacji.  
  
- Pozycjonowane absolutnie  
  
     <xref:System.Windows.Forms.ToolStrip> Jest podobnie jak inne kontrolki, w tym, że jest umieszczany przez <xref:System.Windows.Forms.Control.Location%2A> właściwość, ma stały rozmiar i zazwyczaj uczestniczy w kolejności tabulacji.  
  
#### <a name="keyboard-interaction"></a>Interakcji klawiatury  
  
##### <a name="access-keys"></a>Klucze dostępu  
 W połączeniu z lub klawisz ALT, klucz dostępu jest jednym ze sposobów, aby aktywować kontrolki przy użyciu klawiatury. <xref:System.Windows.Forms.ToolStrip> obsługuje oba klucze dostępu jawne i niejawne. Jawna definicja używa handlowe "i" (&) znak poprzedzający literę. Niejawne definicja używa algorytmu, który próbuje znaleźć pasujący element, na podstawie kolejności znaków w danym `Text` właściwości.  
  
##### <a name="shortcut-keys"></a>Klawisze skrótu  
 Klawisze skrótów używane przez <xref:System.Windows.Forms.MenuStrip> używają kombinacji <xref:System.Windows.Forms.Keys> wyliczenia (co nie jest specyficzne dla zamówienia) do definiowania klawisza skrótu. Można również użyć <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> właściwość do wyświetlenia klawisza skrótu z tekstem, takich jak wyświetlanie "Del" zamiast "Delete".  
  
##### <a name="navigation"></a>Nawigacja  
 Aktywuje klawisz ALT <xref:System.Windows.Forms.MenuStrip> wskazywany przez <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. W tym miejscu, CTRL + TAB powoduje przejście między <xref:System.Windows.Forms.ToolStrip> kontrolki w ramach `ToolStripPanel`s. Naciśnij klawisz TAB lub klawisze strzałek na klawiaturze numerycznej przechodzenie między elementami w <xref:System.Windows.Forms.ToolStrip>. Specjalny algorytm obsługuje nawigacji w regionie przepełnienia. SPACJA zaznacza <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, lub <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### <a name="focus-and-validation"></a>Fokus i sprawdzanie poprawności  
 Po aktywowaniu przez klawisz ALT <xref:System.Windows.Forms.MenuStrip> lub <xref:System.Windows.Forms.ToolStrip> zazwyczaj ani wykonać ani usunąć fokus z formantu, który aktualnie ma fokus. Jeśli jest formantem obsługiwanym w ramach <xref:System.Windows.Forms.MenuStrip> lub lista rozwijana z <xref:System.Windows.Forms.MenuStrip>, formant uzyska fokus, gdy użytkownik naciśnie klawisz TAB. Ogólnie rzecz biorąc <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, i <xref:System.Windows.Forms.Control.Leave> zdarzenia <xref:System.Windows.Forms.MenuStrip> nie może zostać wywołane, uaktywnienie klawiatury. W takiej sytuacji należy użyć <xref:System.Windows.Forms.MenuStrip.MenuActivate> i <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> zdarzenia zamiast tego.  
  
 Domyślnie <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> jest `false`. Wywołaj <xref:System.Windows.Forms.ContainerControl.Validate%2A> jawnie w formularzu do wykonywania sprawdzania poprawności.  
  
#### <a name="layout"></a>Układ  
 Możesz kontrolować <xref:System.Windows.Forms.ToolStrip> układu, wybierając jeden z elementów członkowskich <xref:System.Windows.Forms.ToolStripLayoutStyle> z <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwości.  
  
##### <a name="stack-layouts"></a>Układy stosu  
 Łączenie urządzeń jest rozmieszczanie elementów obok siebie na obu końcach <xref:System.Windows.Forms.ToolStrip>. Na poniższej liście opisano układy stosu.  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> jest ustawieniem domyślnym. To ustawienie powoduje, że <xref:System.Windows.Forms.ToolStrip> zmieniać jego układ automatycznie zgodnie z <xref:System.Windows.Forms.ToolStrip.Orientation%2A> właściwości do obsługi przeciągania i dokowanie scenariuszy.  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> renderuje <xref:System.Windows.Forms.ToolStrip> elementy obok siebie w pionie.  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> renderuje <xref:System.Windows.Forms.ToolStrip> elementy obok siebie w poziomie.  
  
##### <a name="other-features-of-stack-layouts"></a>Inne funkcje stosu układów  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Określa koniec <xref:System.Windows.Forms.ToolStrip> do którego element jest wyrównany.  
  
 Jeśli elementy nie mieszczą się w ramach <xref:System.Windows.Forms.ToolStrip>, automatycznie pojawi się przycisk przepełnienia. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> Ustawienie właściwości określa, czy element jest wyświetlany w obszarze przepełnienia zawsze, zgodnie z potrzebami lub nigdy.  
  
 W <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzenia, można sprawdzić <xref:System.Windows.Forms.ToolStripItem.Placement%2A> właściwości w celu określenia, czy element został umieszczony w głównym <xref:System.Windows.Forms.ToolStrip>, przeciążenia <xref:System.Windows.Forms.ToolStrip>, lub jeśli nie jest obecnie widoczny w ogóle. Typowe przyczyny, dlaczego nie jest wyświetlany element to, że element nie mieści się w głównym <xref:System.Windows.Forms.ToolStrip> i jego <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> właściwość <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.  
  
 Wprowadź <xref:System.Windows.Forms.ToolStrip> ruchome przez umieszczenie go w <xref:System.Windows.Forms.ToolStripPanel> i ustawienie jej <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> do <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.  
  
##### <a name="other-layout-options"></a>Inne opcje układu  
 Są także inne opcje układu <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> i <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.  
  
##### <a name="flow-layout"></a>Układ przepływu  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> Układ jest ustawieniem domyślnym dla <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, i <xref:System.Windows.Forms.ToolStripOverflow>. Jest on podobny do <xref:System.Windows.Forms.FlowLayoutPanel>. Funkcje <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> układu są następujące:  
  
- Wszystkie funkcje <xref:System.Windows.Forms.FlowLayoutPanel> są udostępniane przez <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> właściwości. Należy rzutować <xref:System.Windows.Forms.LayoutSettings> klasy <xref:System.Windows.Forms.FlowLayoutSettings> klasy.  
  
- Możesz użyć <xref:System.Windows.Forms.ToolStripItem.Dock%2A> i <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> właściwości w kodzie do wyrównywania elementów w tym wierszu.  
  
- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Właściwość jest ignorowana.  
  
- W <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzenia, można sprawdzić <xref:System.Windows.Forms.ToolStripItem.Placement%2A> właściwości w celu określenia, czy element został umieszczony w głównym <xref:System.Windows.Forms.ToolStrip> lub nie mieszczą się.  
  
- Uchwyt zmiany nie są odtwarzane i w związku z tym <xref:System.Windows.Forms.ToolStrip> w <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> styl układu w <xref:System.Windows.Forms.ToolStripPanel> nie może zostać przeniesiony.  
  
- <xref:System.Windows.Forms.ToolStrip> Przycisku przeciążenia nie są odtwarzane, a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> jest ignorowana.  
  
##### <a name="table-layout"></a>Układ tabeli  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> Układ jest ustawieniem domyślnym dla <xref:System.Windows.Forms.StatusStrip>. Jest on podobny do <xref:System.Windows.Forms.TableLayoutPanel>. Funkcje <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> układu są następujące:  
  
- Wszystkie funkcje <xref:System.Windows.Forms.TableLayoutPanel> są udostępniane przez <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> właściwości. Należy rzutować <xref:System.Windows.Forms.LayoutSettings> klasy <xref:System.Windows.Forms.TableLayoutSettings> klasy.  
  
- Możesz użyć <xref:System.Windows.Forms.ToolStripItem.Dock%2A> i <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> właściwości w kodzie do wyrównywania elementów w komórce tabeli.  
  
- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Właściwość jest ignorowana.  
  
- W <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzenia, można sprawdzić <xref:System.Windows.Forms.ToolStripItem.Placement%2A> właściwości w celu określenia, czy element został umieszczony w głównym <xref:System.Windows.Forms.ToolStrip> lub nie mieszczą się.  
  
- Uchwyt zmiany nie są odtwarzane i w związku z tym <xref:System.Windows.Forms.ToolStrip> w <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> styl układu w <xref:System.Windows.Forms.ToolStripPanel> nie może zostać przeniesiony.  
  
- <xref:System.Windows.Forms.ToolStrip> Przycisku przeciążenia nie są odtwarzane, a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> jest ignorowana.  
  
## <a name="toolstripitem"></a>ToolStripItem  
 W poniższych tematach opisano <xref:System.Windows.Forms.ToolStripItem> i kontrolek, które wynikają z niego.  
  
 <xref:System.Windows.Forms.ToolStripItem> jest abstrakcyjna klasa bazowa dla wszystkich elementów, które bardziej szczegółowo <xref:System.Windows.Forms.ToolStrip>. Następujący obiekt modelu pokazuje <xref:System.Windows.Forms.ToolStripItem> hierarchii dziedziczenia.  
  
 ![Diagram przedstawiający ToolStripItem modelu obiektów.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)  
  
 <xref:System.Windows.Forms.ToolStripItem> klasy albo dziedziczyć bezpośrednio <xref:System.Windows.Forms.ToolStripItem>, lub pośrednio dziedziczyć z <xref:System.Windows.Forms.ToolStripItem> za pośrednictwem <xref:System.Windows.Forms.ToolStripControlHost> lub <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 <xref:System.Windows.Forms.ToolStripItem> Formanty musi być zawarty w <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, lub <xref:System.Windows.Forms.ContextMenuStrip> i nie można dodać bezpośrednio do formularza. Różne klasy kontenera są przeznaczone do wyświetlania odpowiedniego podzestawu <xref:System.Windows.Forms.ToolStripItem> kontrolki.  
  
 Poniższa tabela zawiera listę zasobów <xref:System.Windows.Forms.ToolStripItem> kontrolek i kontenerów, w których będą wyglądać najlepsze. Mimo że dowolny <xref:System.Windows.Forms.ToolStrip> elementu mogą być hostowane w dowolnym <xref:System.Windows.Forms.ToolStrip>-pochodnych kontenera, te elementy zostały zaprojektowane do wyszukiwania najlepsze w następujących kontenerach:  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> nie są wyświetlane w przyborniku projektanta.  
  
|Zamkniętego elementu|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|Tak|Nie|Nie|Nie|Yes|  
|<xref:System.Windows.Forms.ToolStripComboBox>|Yes|Yes|Yes|Nie|Yes|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Yes|Nie|Nie|Yes|Yes|  
|<xref:System.Windows.Forms.ToolStripLabel>|Yes|Nie|Nie|Yes|Yes|  
|<xref:System.Windows.Forms.ToolStripSeparator>|Yes|Yes|Yes|Nie|Yes|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Yes|Nie|Nie|Yes|Yes|  
|<xref:System.Windows.Forms.ToolStripTextBox>|Yes|Yes|Yes|Nie|Yes|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Nie|Yes|Yes|Nie|Nie|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Nie|Nie|Nie|Yes|Nie|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Yes|Nie|Nie|Yes|Nie|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Yes|Yes|Nie|Yes|Tak|  
  
### <a name="toolstripbutton"></a>ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> jest element przycisku <xref:System.Windows.Forms.ToolStrip>. Możesz wyświetlić ją przy użyciu różnych stylów obramowania i służy do reprezentowania i Aktywuj stany operacyjne. Można również zdefiniować ma fokus, domyślnie.  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel> Zapewnia funkcje etykiety w <xref:System.Windows.Forms.ToolStrip> kontrolki. <xref:System.Windows.Forms.ToolStripLabel> Przypomina <xref:System.Windows.Forms.ToolStripButton> , nie otrzymuje fokus domyślnie i nie jest renderowana jako nastąpiło wypychanie oraz wyróżnione.  
  
 <xref:System.Windows.Forms.ToolStripLabel> jako element hostowanej obsługuje klucze dostępu.  
  
 Użyj <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, i <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> właściwości <xref:System.Windows.Forms.ToolStripLabel> do obsługi kontroli łącza w <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> jest to wersja <xref:System.Windows.Forms.ToolStripLabel> przeznaczony specjalnie dla <xref:System.Windows.Forms.StatusStrip>. Specjalne funkcje obejmują <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, i <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> Dodaje wiersz poziomy lub pionowy pasek narzędzi lub menu, w zależności od orientacji. Umożliwia grupowanie lub rozróżnienie między elementów, takich jak menu.  
  
 Możesz dodać <xref:System.Windows.Forms.ToolStripSeparator> w czasie projektowania, wybierając je z listy rozwijanej. Jednak możesz również automatycznie utworzyć <xref:System.Windows.Forms.ToolStripSeparator> po wpisaniu łącznika (-) w węźle projektanta szablonu lub w <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metody.  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> jest abstrakcyjna klasa bazowa dla <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, i <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost> może obsługiwać inne kontrolki, w tym niestandardowych formantów na dwa sposoby:  
  
- Konstruowania <xref:System.Windows.Forms.ToolStripControlHost> z klasą, która pochodzi od klasy <xref:System.Windows.Forms.Control>. Aby w pełni hostowanych kontrola dostępu i właściwości, należy rzutować <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> właściwości do rzeczywistej klasy reprezentuje.  
  
- Rozszerzanie <xref:System.Windows.Forms.ToolStripControlHost>, a w klasie dziedziczonej domyślnego konstruktora, należy wywołać konstruktora klasy bazowej, przekazując klasę, która pochodzi od klasy <xref:System.Windows.Forms.Control>. Ta opcja pozwala opakować typowych metod kontroli i właściwości, aby mieć łatwy dostęp w <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> jest <xref:System.Windows.Forms.ComboBox> zoptymalizowane pod kątem hostingu w <xref:System.Windows.Forms.ToolStrip>. Podzbiór właściwości i zdarzenia obsługiwanego formantu są widoczne w <xref:System.Windows.Forms.ToolStripComboBox> poziomu, ale podstawowe <xref:System.Windows.Forms.ComboBox> kontrolka jest w pełni dostępne za pośrednictwem <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> właściwości.  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> jest <xref:System.Windows.Forms.TextBox> zoptymalizowane pod kątem hostingu w <xref:System.Windows.Forms.ToolStrip>. Podzbiór właściwości i zdarzenia obsługiwanego formantu są widoczne w <xref:System.Windows.Forms.ToolStripTextBox> poziomu, ale podstawowe <xref:System.Windows.Forms.TextBox> kontrolka jest w pełni dostępne za pośrednictwem <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> właściwości.  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> jest <xref:System.Windows.Forms.ProgressBar> zoptymalizowane pod kątem hostingu w <xref:System.Windows.Forms.ToolStrip>. Podzbiór właściwości i zdarzenia obsługiwanego formantu są widoczne w <xref:System.Windows.Forms.ToolStripProgressBar> poziomu, ale podstawowe <xref:System.Windows.Forms.ProgressBar> kontrolka jest w pełni dostępne za pośrednictwem <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> właściwości.  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> jest abstrakcyjna klasa bazowa dla <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, i <xref:System.Windows.Forms.ToolStripSplitButton>, który może obsługiwać elementy bezpośrednio lub hosta dodatkowe elementy w kontenerze listy rozwijanej. Możesz to zrobić, ustawiając <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> właściwości <xref:System.Windows.Forms.ToolStripDropDown> i ustawienie <xref:System.Windows.Forms.ToolStrip.Items%2A> właściwość <xref:System.Windows.Forms.ToolStripDropDown>. Dostęp do tych elementów listy rozwijanej bezpośrednio za pomocą <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> właściwości.  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> jest <xref:System.Windows.Forms.ToolStripDropDownItem> działające z <xref:System.Windows.Forms.ToolStripDropDownMenu> i <xref:System.Windows.Forms.ContextMenuStrip> do obsługi specjalnych rozmieszczenie wyróżniania, układ i kolumny menu.  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> wygląda jak <xref:System.Windows.Forms.ToolStripButton>, ale pokazuje obszaru listy rozwijanej, po kliknięciu przez użytkownika. Ukrywanie lub pokazywanie strzałkę listy rozwijanej, ustawiając <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> właściwości. <xref:System.Windows.Forms.ToolStripDropDownButton> hosty <xref:System.Windows.Forms.ToolStripOverflowButton> wyświetlającą elementy, które overflow <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripsplitbutton"></a>ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> przycisk łączy i funkcjonalność przycisk listy rozwijanej.  
  
 Użyj <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> właściwości, aby zsynchronizować <xref:System.Windows.Forms.Control.Click> zdarzenia wybranego elementu listy rozwijanej z elementem wyświetlany na przycisku.  
  
### <a name="toolstripitem-generic-features"></a>Funkcje ogólne ToolStripItem  
 <xref:System.Windows.Forms.ToolStripItem> udostępnia następujące funkcje ogólny i opcje dziedziczenia kontrolki:  
  
- Podstawowe zdarzenia  
  
- Obsługa obrazów  
  
- Wyrównanie  
  
- Relacja tekstu i obrazów  
  
- Styl wyświetlania  
  
#### <a name="core-events"></a>Podstawowe zdarzenia  
 <xref:System.Windows.Forms.ToolStripItem> Formanty własne kliknij przycisk, mysz i paint zdarzenia i mogą wykonywać niektóre klawiatury również przetwarzania wstępnego.  
  
#### <a name="image-handling"></a>Obsługa obrazów  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, I <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> właściwości odnoszą się do różnych aspektów programu obsługi obrazów. Korzystanie z obrazów w <xref:System.Windows.Forms.ToolStrip> kontroli przez ustawienie tych właściwości, bezpośrednio lub przez ustawienie Uruchom czas — tylko do <xref:System.Windows.Forms.ToolStrip.ImageList%2A> właściwości.  
  
 Skalowanie obrazów jest określany przez interakcję właściwości w obu <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripItem>, wykonując następujące czynności:  
  
- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> Skala finalnego obrazu określone przez kombinację obrazu <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> ustawienie i kontenera <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> ustawienie.  
  
    - Jeśli <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> jest `true` (ustawienie domyślne) i <xref:System.Windows.Forms.ToolStripItemImageScaling> jest <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, skalowanie obrazów nie występuje i <xref:System.Windows.Forms.ToolStrip> rozmiar jest największego elementu lub realizowania minimalnego rozmiaru.  
  
    - Jeśli <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> jest `false` i <xref:System.Windows.Forms.ToolStripItemImageScaling> jest <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, ani obraz ani <xref:System.Windows.Forms.ToolStrip> skalowanie występuje.  
  
#### <a name="alignment"></a>Wyrównanie  
 Wartość <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwość określa koniec <xref:System.Windows.Forms.ToolStrip> na widocznego elementu. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Właściwość działa tylko wtedy, gdy styl układu <xref:System.Windows.Forms.ToolStrip> jest ustawiony na jedną z wartości przepełnienia stosu.  
  
 Elementy są umieszczone na <xref:System.Windows.Forms.ToolStrip> w kolejności, w której elementy są wyświetlane w kolekcji elementów. Aby programowo zmienić, gdy element jest poukładany, należy użyć <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> metodę, aby przenieść element w kolekcji. Ta metoda powoduje przeniesienie elementu, ale nie jest duplikatem.  
  
#### <a name="text-and-image-relationship"></a>Tekst i obraz relacji  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Właściwość określa względne położenie obrazu w odniesieniu do tekstu na <xref:System.Windows.Forms.ToolStripItem>. Elementy, które nie mają obraz i tekst są traktowane jako specjalne przypadki, aby <xref:System.Windows.Forms.ToolStripItem> nie wyświetla puste miejscu brakującego elementu lub elementów.  
  
#### <a name="display-style"></a>Styl wyświetlania  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Umożliwia ustawienie wartości właściwości elementów tekstowych i obrazów podczas wyświetlania tylko chcesz. Zazwyczaj służy do zmiany tylko styl wyświetlania, gdy ten sam element są wyświetlane w innym kontekście.  
  
## <a name="accessory-classes"></a>Akcesoriów klas  
 Klasy, które zapewniają różne inne funkcje obejmują:  
  
- <xref:System.Windows.Forms.ToolStripManager> obsługuje <xref:System.Windows.Forms.ToolStrip>-powiązane zadania dla całej aplikacji, takich jak opcje scalania, ustawienia i renderowania.  
  
- <xref:System.Windows.Forms.ToolStripRenderer> Umożliwia zastosowanie określony styl lub motyw do <xref:System.Windows.Forms.ToolStrip> łatwe.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer> Tworzy pióra i pędzle, na podstawie tabeli kolorów wymienne (<xref:System.Windows.Forms.ProfessionalColorTable>).  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer> stosuje się kolory systemowe i styl płaskie visual <xref:System.Windows.Forms.ToolStrip> aplikacji.  
  
- <xref:System.Windows.Forms.ToolStripContainer> jest podobny do <xref:System.Windows.Forms.SplitContainer>. Używa czterech paneli zadokowany po stronie (wystąpienia <xref:System.Windows.Forms.ToolStripPanel>) i jeden panel centralnej (wystąpienie <xref:System.Windows.Forms.ToolStripContentPanel>) do utworzenia typowy układ. Nie można usunąć panele po stronie, ale można je ukryć. Nie można usunąć ani ukryć panel centralnej. Można rozmieścić co najmniej jeden <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, lub <xref:System.Windows.Forms.StatusStrip> kontrolki w panelach po stronie, a za pomocą centralnej panelu dla innych kontrolek. <xref:System.Windows.Forms.ToolStripContentPanel> Także sposób, aby uzyskać pomoc techniczną renderowania w treści formularza w taki sposób, aby uzyskać spójny wygląd. <xref:System.Windows.Forms.ToolStripContainer> nie obsługuje interfejsu wielu dokumentów (MDI).  
  
- <xref:System.Windows.Forms.ToolStripPanel> udostępnia miejsce do przenoszenia i rozmieszczanie <xref:System.Windows.Forms.ToolStrip> kontrolki. Jeśli tak, można użyć tylko jeden panelu i <xref:System.Windows.Forms.ToolStripPanel> działa dobrze w scenariuszach MDI.  
  
## <a name="see-also"></a>Zobacz także

- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md)
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
- [MenuStrip, kontrolka](menustrip-control-windows-forms.md)
- [StatusStrip, kontrolka](statusstrip-control.md)
- [ContextMenuStrip, kontrolka](contextmenustrip-control.md)
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
