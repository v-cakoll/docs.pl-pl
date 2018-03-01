---
title: "ToolStrip — Architektura formantu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b112cb1e383b092c1bcc4403e04938b3b83c5ecc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="toolstrip-control-architecture"></a>ToolStrip — Architektura formantu
<xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripItem> klasy zapewniają elastyczny i rozszerzalny system do wyświetlania elementów paska narzędzi, stanu i menu. Te klasy są zawarte w <xref:System.Windows.Forms> przestrzeni nazw, a wszystkie nazwy z prefiksem "ToolStrip" (takie jak <xref:System.Windows.Forms.ToolStripOverflow>) lub z sufiksem "Usuń" (takie jak <xref:System.Windows.Forms.MenuStrip>).  
  
## <a name="toolstrip"></a>ToolStrip  
 W poniższych tematach opisano <xref:System.Windows.Forms.ToolStrip> i formantów, które dziedziczą z niego.  
  
 <xref:System.Windows.Forms.ToolStrip>jest abstrakcyjna klasa podstawowa dla <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, i <xref:System.Windows.Forms.ContextMenuStrip>. Następujący obiekt modelu pokazuje <xref:System.Windows.Forms.ToolStrip> hierarchii dziedziczenia.  
  
 ![Model obiektu ToolStrip](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.gif "ToolStripObjectModel")  
Model obiektu ToolStrip  
  
 Można uzyskać dostępu do wszystkich elementów w <xref:System.Windows.Forms.ToolStrip> za pośrednictwem <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekcji. Można uzyskać dostępu do wszystkich elementów w <xref:System.Windows.Forms.ToolStripDropDownItem> za pośrednictwem <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> kolekcji. W klasie pochodnej z <xref:System.Windows.Forms.ToolStrip>, można również użyć <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> właściwość, aby uzyskać dostęp tylko tych elementów, które są aktualnie wyświetlane. Są to elementy, które nie są obecnie menu przeciążenia.  
  
 Następujące elementy zostały zaprojektowane specjalnie współpracuje z obu <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> w wszystkie orientacje. Są one domyślnie dostępne w czasie projektowania dla <xref:System.Windows.Forms.ToolStrip> sterowania:  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip>jest kontenerem najwyższego poziomu, która zastępuje <xref:System.Windows.Forms.MainMenu>. Umożliwia także Obsługa kluczy i zarządzania dokumentami wiele funkcji interfejsu (MDI). Funkcjonalnie <xref:System.Windows.Forms.ToolStripDropDownItem> i <xref:System.Windows.Forms.ToolStripMenuItem> pracy wraz z <xref:System.Windows.Forms.MenuStrip>, mimo że pochodzą one od <xref:System.Windows.Forms.ToolStripItem>.  
  
 Następujące elementy zostały zaprojektowane specjalnie współpracuje z obu <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> w wszystkie orientacje. Są one domyślnie dostępne w czasie projektowania dla <xref:System.Windows.Forms.MenuStrip> sterowania:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip>zastępuje <xref:System.Windows.Forms.StatusBar> formantu. Specjalne funkcje <xref:System.Windows.Forms.StatusStrip> obejmują układu tabeli niestandardowych, obsługę zmiany rozmiaru i przenoszenie grips, formularza i `Spring` właściwość, która umożliwia <xref:System.Windows.Forms.ToolStripStatusLabel> celu wypełnienia dostępnego miejsca w automatycznie.  
  
 Następujące elementy zostały zaprojektowane specjalnie współpracuje z obu <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> w wszystkie orientacje. Są one domyślnie dostępne w czasie projektowania dla <xref:System.Windows.Forms.StatusStrip> sterowania:  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip>zastępuje <xref:System.Windows.Forms.ContextMenu>. Możesz skojarzyć <xref:System.Windows.Forms.ContextMenuStrip> z żadnym formantem i prawym przyciskiem myszy kliknij automatycznie wyświetla menu kontekstowe (lub menu skrótów). Można wyświetlić <xref:System.Windows.Forms.ContextMenuStrip> programowo przy użyciu <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> metody. <xref:System.Windows.Forms.ContextMenuStrip>obsługuje można anulować <xref:System.Windows.Forms.ToolStripDropDown.Opening> i <xref:System.Windows.Forms.ToolStripDropDown.Closing> zdarzenia do obsługi dynamicznej populacji i kliknij wielu scenariuszy. <xref:System.Windows.Forms.ContextMenuStrip>obsługuje obrazy, stan zaznaczenia elementu menu tekstu, klucze dostępu, skróty i menu kaskadowych.  
  
 Następujące elementy zostały zaprojektowane specjalnie współpracuje z obu <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> w wszystkie orientacje. Są one domyślnie dostępne w czasie projektowania dla <xref:System.Windows.Forms.ContextMenuStrip> sterowania:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>Funkcje ogólne ToolStrip  
 W poniższych tematach opisano funkcje i zachowanie, które są ogólnego na <xref:System.Windows.Forms.ToolStrip> i zostały opracowane kontrolki.  
  
#### <a name="painting"></a>Malowanie  
 Malowanie niestandardowych można zrobić w <xref:System.Windows.Forms.ToolStrip> formantów na kilka sposobów. Podobnie jak w przypadku innych formantów formularzy systemu Windows <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripItem> mają możliwym do zastąpienia `OnPaint` metod i `Paint` zdarzenia. Podobnie jak w regularnych rysowania współrzędnych jest względem obszaru klienckiego formantu; oznacza to, w lewym górnym rogu formantu jest równa 0, 0. `Paint` Zdarzeń i `OnPaint` metodę <xref:System.Windows.Forms.ToolStripItem> zachowują się podobnie jak inne zdarzenia malowanie formantu.  
  
 <xref:System.Windows.Forms.ToolStrip> Elementy sterujące udostępniają również bardziej precyzyjną dostęp do renderowania elementów i kontenerze, za pośrednictwem <xref:System.Windows.Forms.ToolStripRenderer> klasy, która ma nadpisywalnych metod dla malowania tła, tła elementu, obrazu elementu, element strzałkę, tekst elementu, a obramowaniem <xref:System.Windows.Forms.ToolStrip>. Argumenty zdarzenia dla tych metod ujawnia kilka właściwości, takie jak prostokąty, kolory i formatach tekstowych, które można dostosować zgodnie z potrzebami.  
  
 Aby dostosować kilka aspektów jak jest malowany element, zazwyczaj przesłonięcia <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Pisania nowy element, aby kontrolować wszystkich aspektów malowania zastępują `OnPaint` metody. Z poziomu `OnPaint`, można użyć metody <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Domyślnie <xref:System.Windows.Forms.ToolStrip> jest podwójne buforowane, korzystanie z zalet <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> ustawienie.  
  
#### <a name="parenting"></a>Elementy nadrzędne  
 Koncepcja własności kontenera i element nadrzędny jest bardziej złożone w <xref:System.Windows.Forms.ToolStrip> formantów niż w inne formanty kontenera formularzy systemu Windows. Jest niezbędne do obsługi dynamicznej scenariuszy, takich jak przepełnienie Udostępnianie elementów listy rozwijanej w wielu <xref:System.Windows.Forms.ToolStrip> elementów i obsługuje generowania <xref:System.Windows.Forms.ContextMenuStrip> z formantu.  
  
 Poniższa lista zawiera opis elementów członkowskich powiązany element nadrzędny i wyjaśniono ich używania.  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>uzyskuje dostęp do elementu, który jest źródłem elementu listy rozwijanej. Jest to podobne do <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, ale zamiast zwracać formantu, zwraca <xref:System.Windows.Forms.ToolStripItem>.  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>Określa formant, który jest źródłem z <xref:System.Windows.Forms.ContextMenuStrip> po wielu formantów udostępnianie takie same <xref:System.Windows.Forms.ContextMenuStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>jest metodą dostępu tylko do odczytu do <xref:System.Windows.Forms.ToolStripItem.Parent%2A> właściwości. Element nadrzędny różni się od właściciela, że nadrzędne oznacza zwrócony bieżącego <xref:System.Windows.Forms.ToolStrip> , w której element jest wyświetlany, która może znajdować się w obszarze przepełnienia.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A>Zwraca <xref:System.Windows.Forms.ToolStrip> kolekcji elementów, których zawiera bieżącą <xref:System.Windows.Forms.ToolStripItem>. Jest to najlepszy sposób, aby odwołać <xref:System.Windows.Forms.ToolStrip.ImageList%2A> lub innych właściwości w najwyższego poziomu <xref:System.Windows.Forms.ToolStrip> bez pisania kodu specjalne obsłużyć przepełnienia.  
  
#### <a name="behavior-of-inherited-controls"></a>Zachowanie dziedziczone formantów  
 Poniższych formantów są zablokowane, gdy są one używane w dziedziczeniu:  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>zawiera panele na <xref:System.Windows.Forms.ToolStripContainer> , a także poszczególne <xref:System.Windows.Forms.ToolStripPanel> kontrolki.  
  
 Na przykład można utworzyć nowej aplikacji formularzy systemu Windows przy użyciu co najmniej jedna z kontrolek na poprzedniej liście. Modyfikator dostępu elementu jeden lub kilka formantów, aby ustawić `public` lub `protected`, a następnie skompilować projekt. Dodaj formularz, który dziedziczy pierwszy formularz, a następnie wybierz kontrolkę dziedziczone. Ten formant jest widoczny zablokowanym zachowuje się tak, jakby była jego modyfikator dostępu `private`.  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>Obsługa elementu ToolStripContainer dziedziczenia  
 <xref:System.Windows.Forms.ToolStripContainer> Sterowanie obsługuje niewiele scenariuszy dziedziczone, podobnie do poniższego przykładu:  
  
1.  Tworzenie nowej aplikacji formularzy systemu Windows.  
  
2.  Dodaj <xref:System.Windows.Forms.ToolStripContainer> do formularza.  
  
3.  Ustaw modyfikator dostępu elementu <xref:System.Windows.Forms.ToolStripContainer> do `public` lub `protected`.  
  
4.  Dodaj dowolną kombinację <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.ContextMenuStrip> formanty <xref:System.Windows.Forms.ToolStripPanel> regionów <xref:System.Windows.Forms.ToolStripContainer>.  
  
5.  Skompiluj projekt.  
  
6.  Dodaj formularz, który dziedziczy z pierwszego formularza.  
  
7.  Wybierz dziedziczonego <xref:System.Windows.Forms.ToolStripContainer> w formularzu.  
  
#### <a name="inherited-behavior-of-child-controls"></a>Dziedziczony zachowanie formantów podrzędnych  
 Po wykonaniu poprzednich kroków spowoduje następujące dziedziczone zachowanie:  
  
-   W Projektancie formantu jest wyświetlana ikona dziedziczone.  
  
-   <xref:System.Windows.Forms.ToolStripPanel> Formantów jest zablokowany; nie można wybrać ani zmienić ich zawartość.  
  
-   Można dodawać formanty do <xref:System.Windows.Forms.ToolStripContentPanel>, Przenieś formanty i były formanty podrzędne <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
-   Utrwalić zmiany po utworzeniu formularza.  
  
    > [!NOTE]
    >  Usuń modyfikatorów dostępu ze wszystkich <xref:System.Windows.Forms.ToolStripPanel> formantów, które są częścią <xref:System.Windows.Forms.ToolStripContainer>. Modyfikator dostępu elementu <xref:System.Windows.Forms.ToolStripContainer> reguluje całego formantu.  
  
#### <a name="partial-trust"></a>Zaufanie częściowe  
 Ograniczenia `ToolStrip`s w częściowej relacji zaufania są zaprojektowane, aby zapobiec niepotrzebnemu wprowadzania informacji osobistych, które mogą być używane przez nieautoryzowane osoby lub usługi. Środków ochronnych są następujące:  
  
-   `ToolStripDropDown`Formanty wymagają <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> do wyświetlania elementów w <xref:System.Windows.Forms.ToolStripControlHost>. Dotyczy to zarówno wewnętrzne formanty takie jak <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, i <xref:System.Windows.Forms.ToolStripProgressBar> jak również, aby utworzyć użytkownika kontrolki. Jeśli to wymaganie nie jest spełniony, te elementy nie są wyświetlane. Nie wyjątek.  
  
-   Ustawienie <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> właściwości `false` nie jest dozwolona i można anulować <xref:System.Windows.Forms.ToolStripDropDown.Closing> parametr zdarzenia jest ignorowana. Dzięki temu można wprowadzić więcej niż jednym naciśnięciem klawisza bez odrzucanie elementu listy rozwijanej. Jeśli to wymaganie nie są spełnione, nie są wyświetlane takie elementy. Nie wyjątek.  
  
-   Wiele naciśnięcie klawisza Obsługa zdarzeń nie zostanie wygenerowany, jeśli występują one w częściowej relacji zaufania kontekstów innych niż <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.  
  
-   Klawisze dostępu nie są przetwarzane, gdy <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> nie udzielono.  
  
#### <a name="usage"></a>Użycie  
 Następujące wzorców użycia mają wpływ na <xref:System.Windows.Forms.ToolStrip> układu, klawiatury i zachowanie użytkownika końcowego:  
  
-   W<xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip> Można zmienić ich pozycji w <xref:System.Windows.Forms.ToolStripPanel> i wielu <xref:System.Windows.Forms.ToolStripPanel>s. `Dock` Właściwość jest ignorowana, a jeśli <xref:System.Windows.Forms.ToolStrip.Stretch%2A> właściwość jest `false`, rozmiar <xref:System.Windows.Forms.ToolStrip> zwiększa się w miarę elementy są dodawane do <xref:System.Windows.Forms.ToolStripPanel>. Zazwyczaj <xref:System.Windows.Forms.ToolStrip> nie uczestniczy w kolejności tabulacji.  
  
-   Zadokowane  
  
     <xref:System.Windows.Forms.ToolStrip> Jest umieszczona na jednej stronie kontenera w stałej pozycji i rozmiaru rozszerza się na cały krawędzi, z którym jest zadokowany. Zazwyczaj <xref:System.Windows.Forms.ToolStrip> nie uczestniczy w kolejności tabulacji.  
  
-   Bezwzględnego  
  
     <xref:System.Windows.Forms.ToolStrip> Jest tak, jak inne formanty, w którym znajduje się przez <xref:System.Windows.Forms.Control.Location%2A> właściwość ma stały rozmiar i zwykle uczestniczy w kolejności tabulacji.  
  
#### <a name="keyboard-interaction"></a>Klawiatury  
  
##### <a name="access-keys"></a>Klawisze dostępu  
 W połączeniu z lub klawisz ALT, klucze dostępu są jednym ze sposobów aktywować formantu za pomocą klawiatury. <xref:System.Windows.Forms.ToolStrip>obsługuje zarówno klucze dostępu jawne i niejawne. Jawna definicja używa handlowego "i" (&) znaków poprzedzających literę. Definicja niejawne używa algorytmu, który próbuje odnaleźć pasującego elementu na podstawie kolejności znaków w danym `Text` właściwości.  
  
##### <a name="shortcut-keys"></a>Klawisze skrótu  
 Klawisze skrótu używany przez <xref:System.Windows.Forms.MenuStrip> jest użycie kombinacji <xref:System.Windows.Forms.Keys> — wyliczenie (który nie jest specyficzne dla kolejności) do definiowania klawisz skrótu. Można również użyć <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> właściwość, aby wyświetlić klawisza skrótu z tekstem, takie jak wyświetlanie "Del" zamiast "Delete".  
  
##### <a name="navigation"></a>Nawigacji  
 Aktywuje klawisz ALT <xref:System.Windows.Forms.MenuStrip> wskazywana przez <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. Dostępne klawisze CTRL + TAB przechodzi między <xref:System.Windows.Forms.ToolStrip> steruje w obrębie `ToolStripPanel`s. Klawisz TAB lub klawisze strzałek na klawiaturze numerycznej przechodzenie między elementami w <xref:System.Windows.Forms.ToolStrip>. Specjalny algorytm obsługuje nawigacji w obszarze przepełnienia. Wybiera spacja <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, lub <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### <a name="focus-and-validation"></a>Fokus i sprawdzania poprawności  
 Uaktywnienie klawisz ALT, <xref:System.Windows.Forms.MenuStrip> lub <xref:System.Windows.Forms.ToolStrip> zazwyczaj nie wykonać ani nie usuwać fokus formant, który aktualnie ma fokus. Jeśli jest obsługiwany przez formant <xref:System.Windows.Forms.MenuStrip> lub lista rozwijana z <xref:System.Windows.Forms.MenuStrip>, formant uzyska fokus, gdy użytkownik naciśnie klawisz TAB. Ogólnie rzecz biorąc <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, i <xref:System.Windows.Forms.Control.Leave> zdarzenia <xref:System.Windows.Forms.MenuStrip> nie może zostać wywołane, uaktywnienie klawiatury. W takiej sytuacji należy użyć <xref:System.Windows.Forms.MenuStrip.MenuActivate> i <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> zdarzenia zamiast tego.  
  
 Domyślnie <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> jest `false`. Wywołanie <xref:System.Windows.Forms.ContainerControl.Validate%2A> jawnie na formularzu do sprawdzania poprawności.  
  
#### <a name="layout"></a>Układ  
 Możesz kontrolować <xref:System.Windows.Forms.ToolStrip> układu, wybierając jedną z elementów członkowskich <xref:System.Windows.Forms.ToolStripLayoutStyle> z <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwości.  
  
##### <a name="stack-layouts"></a>Układy stosu  
 Układania jest rozmieszczanie elementów obok siebie na obu końcach <xref:System.Windows.Forms.ToolStrip>. Poniżej przedstawiono listę układów stosu.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow>jest ustawieniem domyślnym. To ustawienie powoduje <xref:System.Windows.Forms.ToolStrip> zmienić jego układ automatycznie zgodnie z <xref:System.Windows.Forms.ToolStrip.Orientation%2A> właściwości do obsługi przeciągania i dokowanie scenariuszy.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>renderuje <xref:System.Windows.Forms.ToolStrip> elementy w pionie obok siebie.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>renderuje <xref:System.Windows.Forms.ToolStrip> elementy w poziomie obok siebie.  
  
##### <a name="other-features-of-stack-layouts"></a>Inne funkcje układów stosu  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>Określa koniec <xref:System.Windows.Forms.ToolStrip> do którego element jest wyrównany.  
  
 Gdy elementy mieści się w <xref:System.Windows.Forms.ToolStrip>, automatycznie zostanie wyświetlony przycisku przeciążenia. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> Właściwości ustawienie określa, czy element jest wyświetlany w obszarze przepełnienia zawsze, zgodnie z potrzebami lub nigdy.  
  
 W <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzeń, możesz sprawdzić <xref:System.Windows.Forms.ToolStripItem.Placement%2A> właściwości w celu określenia, czy element został umieszczony w głównym <xref:System.Windows.Forms.ToolStrip>, przeciążenia <xref:System.Windows.Forms.ToolStrip>, lub jeśli nie jest obecnie widoczny w ogóle. Typowe przyczyny, dlaczego nie jest wyświetlany element są, że element nie mieszczą się w głównym <xref:System.Windows.Forms.ToolStrip> i jego <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> ustawiono właściwość <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.  
  
 Należy <xref:System.Windows.Forms.ToolStrip> ruchomy przy <xref:System.Windows.Forms.ToolStripPanel> i ustawienie jej <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> do <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.  
  
##### <a name="other-layout-options"></a>Inne opcje układu  
 Inne opcje układu są <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> i <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.  
  
##### <a name="flow-layout"></a>Układ przepływu  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>wartością domyślną jest układu <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, i <xref:System.Windows.Forms.ToolStripOverflow>. Jest on podobny do <xref:System.Windows.Forms.FlowLayoutPanel>. Funkcje <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> układu są następujące:  
  
-   Wszystkie funkcje <xref:System.Windows.Forms.FlowLayoutPanel> są udostępniane przez <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> właściwości. Należy rzutować <xref:System.Windows.Forms.LayoutSettings> klasy do <xref:System.Windows.Forms.FlowLayoutSettings> klasy.  
  
-   Można użyć <xref:System.Windows.Forms.ToolStripItem.Dock%2A> i <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> właściwości w kodzie, aby były wyrównane elementów w wierszu.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Właściwość jest ignorowana.  
  
-   W <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzeń, możesz sprawdzić <xref:System.Windows.Forms.ToolStripItem.Placement%2A> właściwości w celu określenia, czy element został umieszczony w głównym <xref:System.Windows.Forms.ToolStrip> lub nie mieszczą się.  
  
-   Uchwytu nie są odtwarzane i w związku z tym <xref:System.Windows.Forms.ToolStrip> w <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> stylu układu w <xref:System.Windows.Forms.ToolStripPanel> nie może zostać przeniesiony.  
  
-   <xref:System.Windows.Forms.ToolStrip> Przycisku przeciążenia nie są odtwarzane, a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> jest ignorowana.  
  
##### <a name="table-layout"></a>Układ tabeli  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>wartością domyślną jest układu <xref:System.Windows.Forms.StatusStrip>. Jest on podobny do <xref:System.Windows.Forms.TableLayoutPanel>. Funkcje <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> układu są następujące:  
  
-   Wszystkie funkcje <xref:System.Windows.Forms.TableLayoutPanel> są udostępniane przez <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> właściwości. Należy rzutować <xref:System.Windows.Forms.LayoutSettings> klasy do <xref:System.Windows.Forms.TableLayoutSettings> klasy.  
  
-   Można użyć <xref:System.Windows.Forms.ToolStripItem.Dock%2A> i <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> właściwości w kodzie, aby były wyrównane elementów w komórce tabeli.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Właściwość jest ignorowana.  
  
-   W <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzeń, możesz sprawdzić <xref:System.Windows.Forms.ToolStripItem.Placement%2A> właściwości w celu określenia, czy element został umieszczony w głównym <xref:System.Windows.Forms.ToolStrip> lub nie mieszczą się.  
  
-   Uchwytu nie są odtwarzane i w związku z tym <xref:System.Windows.Forms.ToolStrip> w <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> stylu układu w <xref:System.Windows.Forms.ToolStripPanel> nie może zostać przeniesiony.  
  
-   <xref:System.Windows.Forms.ToolStrip> Przycisku przeciążenia nie są odtwarzane, a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> jest ignorowana.  
  
## <a name="toolstripitem"></a>ToolStripItem  
 W poniższych tematach opisano <xref:System.Windows.Forms.ToolStripItem> i formantów, które dziedziczą z niego.  
  
 <xref:System.Windows.Forms.ToolStripItem>jest abstrakcyjna klasa podstawowa dla wszystkich elementów, które wchodzą w <xref:System.Windows.Forms.ToolStrip>. Następujący obiekt modelu pokazuje <xref:System.Windows.Forms.ToolStripItem> hierarchii dziedziczenia.  
  
 ![Model obiektu ToolStripItem](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.gif "ToolStripItemObjectModel")  
Model obiektu ToolStripItem  
  
 <xref:System.Windows.Forms.ToolStripItem>klasy albo dziedziczyć bezpośrednio po <xref:System.Windows.Forms.ToolStripItem>, ani pośrednio dziedziczyć z <xref:System.Windows.Forms.ToolStripItem> za pośrednictwem <xref:System.Windows.Forms.ToolStripControlHost> lub <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 <xref:System.Windows.Forms.ToolStripItem>formanty muszą być zawarte w <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, lub <xref:System.Windows.Forms.ContextMenuStrip> i nie można dodać bezpośrednio do formularza. Różne klasy kontenerów mają zawierać odpowiednie <xref:System.Windows.Forms.ToolStripItem> kontrolki.  
  
 Poniższa tabela zawiera listę zasobów <xref:System.Windows.Forms.ToolStripItem> kontrolek i kontenerów, w których Szukaj najlepsze. Mimo że żadnego <xref:System.Windows.Forms.ToolStrip> elementu może być hostowana w żadnym <xref:System.Windows.Forms.ToolStrip>-pochodnych kontenera, te elementy zostały zaprojektowane do wyszukiwania najlepsze w następujących kontenerach:  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown>nie ma w przyborniku projektanta.  
  
|Zamkniętego elementu|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|Element ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|Tak|Nie|Nie|Nie|Tak|  
|<xref:System.Windows.Forms.ToolStripComboBox>|Tak|Tak|Tak|Nie|Tak|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Tak|Nie|Nie|Tak|Tak|  
|<xref:System.Windows.Forms.ToolStripLabel>|Tak|Nie|Nie|Tak|Tak|  
|<xref:System.Windows.Forms.ToolStripSeparator>|Tak|Tak|Tak|Nie|Tak|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Tak|Nie|Nie|Tak|Tak|  
|<xref:System.Windows.Forms.ToolStripTextBox>|Tak|Tak|Tak|Nie|Tak|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Nie|Tak|Tak|Nie|Nie|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Nie|Nie|Nie|Tak|Nie|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Tak|Nie|Nie|Tak|Nie|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Tak|Tak|Nie|Tak|Tak|  
  
### <a name="toolstripbutton"></a>Element ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton>Element przycisku jest <xref:System.Windows.Forms.ToolStrip>. Wyświetl ją przy użyciu różnych stylów obramowania i służy do reprezentowania i Aktywuj stany operacyjne. Można również zdefiniować ma fokus domyślnie.  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel> Oferuje funkcje etykiety w <xref:System.Windows.Forms.ToolStrip> kontrolki. <xref:System.Windows.Forms.ToolStripLabel> Przypomina <xref:System.Windows.Forms.ToolStripButton> który nie uzyska fokus domyślnie i nie jest renderowana jako wciśnięcia lub wyróżniony.  
  
 <xref:System.Windows.Forms.ToolStripLabel>jako element hostowanej obsługuje klucze dostępu.  
  
 Użyj <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, i <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> właściwości <xref:System.Windows.Forms.ToolStripLabel> do obsługi kontroli łączy w <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel>jest to wersja <xref:System.Windows.Forms.ToolStripLabel> przeznaczony specjalnie dla <xref:System.Windows.Forms.StatusStrip>. Specjalne funkcje obejmują <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, i <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### <a name="toolstripseparator"></a>Elementu ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> Dodaje do paska narzędzi lub menu, w zależności od orientację linii pionowych lub poziomych. Umożliwia grupowanie lub różnicy między elementów, takich jak menu.  
  
 Możesz dodać <xref:System.Windows.Forms.ToolStripSeparator> w czasie projektowania, wybierając je z listy rozwijanej. Jednak można automatycznie utworzyć <xref:System.Windows.Forms.ToolStripSeparator> , wpisując łącznik (-) w węźle szablon projektanta lub w <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metody.  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost>jest abstrakcyjna klasa podstawowa dla <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, i <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost>może obsługiwać inne formanty, w tym niestandardowych formantów na dwa sposoby:  
  
-   Utworzyć <xref:System.Windows.Forms.ToolStripControlHost> z klasą pochodzącą z <xref:System.Windows.Forms.Control>. Pełnego dostępu do obsługiwanego formantu i właściwości, należy rzutować <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> właściwości, do rzeczywistych klasy reprezentuje.  
  
-   Rozszerzanie <xref:System.Windows.Forms.ToolStripControlHost>i w dziedziczonej klasie domyślnego konstruktora, wywołanie konstruktora klasy podstawowej przekazywanie klasą pochodzącą z <xref:System.Windows.Forms.Control>. Ta opcja umożliwia zawijać typowe metody kontroli i właściwości, by mieć łatwy dostęp w <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox>jest <xref:System.Windows.Forms.ComboBox> zoptymalizowana pod kątem hostowania w <xref:System.Windows.Forms.ToolStrip>. Podzbiór właściwości i zdarzenia obsługiwanego formantu są widoczne w <xref:System.Windows.Forms.ToolStripComboBox> poziomu, ale odpowiadającego <xref:System.Windows.Forms.ComboBox> formant jest w pełni dostępna za pośrednictwem <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> właściwości.  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox>jest <xref:System.Windows.Forms.TextBox> zoptymalizowana pod kątem hostowania w <xref:System.Windows.Forms.ToolStrip>. Podzbiór właściwości i zdarzenia obsługiwanego formantu są widoczne w <xref:System.Windows.Forms.ToolStripTextBox> poziomu, ale odpowiadającego <xref:System.Windows.Forms.TextBox> formant jest w pełni dostępna za pośrednictwem <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> właściwości.  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar>jest <xref:System.Windows.Forms.ProgressBar> zoptymalizowana pod kątem hostowania w <xref:System.Windows.Forms.ToolStrip>. Podzbiór właściwości i zdarzenia obsługiwanego formantu są widoczne w <xref:System.Windows.Forms.ToolStripProgressBar> poziomu, ale odpowiadającego <xref:System.Windows.Forms.ProgressBar> formant jest w pełni dostępna za pośrednictwem <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> właściwości.  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem>jest abstrakcyjna klasa podstawowa dla <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, i <xref:System.Windows.Forms.ToolStripSplitButton>, który może obsługiwać elementy bezpośrednio lub hosta dodatkowych elementów w kontenerze listy rozwijanej. Możesz to zrobić przez ustawienie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> właściwości <xref:System.Windows.Forms.ToolStripDropDown> i ustawienie <xref:System.Windows.Forms.ToolStrip.Items%2A> właściwość <xref:System.Windows.Forms.ToolStripDropDown>. Dostęp do tych elementów listy rozwijanej bezpośrednio za pomocą <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> właściwości.  
  
### <a name="toolstripmenuitem"></a>Element ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem>jest <xref:System.Windows.Forms.ToolStripDropDownItem> działające z <xref:System.Windows.Forms.ToolStripDropDownMenu> i <xref:System.Windows.Forms.ContextMenuStrip> do obsługi specjalnych rozmieszczenie wyróżnianie, układu i kolumny dla menu.  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton>prawdopodobnie <xref:System.Windows.Forms.ToolStripButton>, ale obszar listy rozwijanej będzie wyświetlana po kliknięciu przez użytkownika. Ukrycie lub pokazanie strzałkę listy rozwijanej przez ustawienie <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> właściwości. <xref:System.Windows.Forms.ToolStripDropDownButton>hosty <xref:System.Windows.Forms.ToolStripOverflowButton> wyświetlającą elementy, które przepełnienie <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripsplitbutton"></a>ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton>przycisk łączy i funkcjonalność przycisku rozwijanego.  
  
 Użyj <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> właściwości, aby zsynchronizować <xref:System.Windows.Forms.Control.Click> zdarzeń wybranego elementu listy rozwijanej z elementem wyświetlany na przycisku.  
  
### <a name="toolstripitem-generic-features"></a>Funkcje ogólne ToolStripItem  
 <xref:System.Windows.Forms.ToolStripItem>udostępnia następujące funkcje ogólne i opcje dziedziczenia kontrolki:  
  
-   Podstawowe zdarzenia  
  
-   Obsługa obrazu  
  
-   Wyrównanie  
  
-   Relacja tekstowych i obrazów  
  
-   Styl wyświetlania  
  
#### <a name="core-events"></a>Podstawowe zdarzenia  
 <xref:System.Windows.Forms.ToolStripItem>Formanty własnych kliknij, mysz i paint zdarzeń i mogą wykonywać niektóre klawiatury również przetwarzania wstępnego.  
  
#### <a name="image-handling"></a>Obsługa obrazu  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, I <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> właściwości odnoszą się do różnych aspektów obsługi obrazów. Obrazy w <xref:System.Windows.Forms.ToolStrip> formantów przez ustawienie tych właściwości bezpośrednio lub przez ustawienie Uruchom czas — tylko do <xref:System.Windows.Forms.ToolStrip.ImageList%2A> właściwości.  
  
 Skalowanie obrazu jest określany przez interakcji właściwości zarówno <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripItem>w następujący sposób:  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>Skala finalnego obrazu określone przez kombinację obrazu <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> ustawienie i kontenera <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> ustawienie.  
  
    -   Jeśli <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> jest `true` (ustawienie domyślne) i <xref:System.Windows.Forms.ToolStripItemImageScaling> jest <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, rozmiar rzeczywisty obraz występuje i <xref:System.Windows.Forms.ToolStrip> rozmiar jest to, że największy element lub wyznaczonych minimalny rozmiar.  
  
    -   Jeśli <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> jest `false` i <xref:System.Windows.Forms.ToolStripItemImageScaling> jest <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, ani obraz ani <xref:System.Windows.Forms.ToolStrip> skalowanie występuje.  
  
#### <a name="alignment"></a>Wyrównanie  
 Wartość <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwość określa koniec <xref:System.Windows.Forms.ToolStrip> na której element. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Właściwość działa tylko wtedy, gdy styl układu <xref:System.Windows.Forms.ToolStrip> ustawiono na jedną z wartości przepełnienia stosu.  
  
 Elementy są umieszczane na <xref:System.Windows.Forms.ToolStrip> w kolejność wyświetlania elementów w kolekcji elementów. Aby programowo zmienić, gdy element jest poukładany, użyj <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> metodę Przenieś element w kolekcji. Ta metoda powoduje przeniesienie elementu, ale nie jest duplikatem.  
  
#### <a name="text-and-image-relationship"></a>Tekst i obraz relacji  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Właściwość określa względne położenie obrazu względem tekstu na <xref:System.Windows.Forms.ToolStripItem>. Elementy, których brakuje obraz i tekst są traktowane jako specjalne przypadki, aby <xref:System.Windows.Forms.ToolStripItem> nie są wyświetlane dla elementów lub Brak elementu puste miejsce.  
  
#### <a name="display-style"></a>Styl wyświetlania  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>Umożliwia ustawienie wartości właściwości elementów tekstowych i obrazów podczas wyświetlania tylko ma. Służy to zwykle zmienić tylko styl wyświetlania przy wyświetlaniu tego samego elementu w różnych kontekstu.  
  
## <a name="accessory-classes"></a>Akcesoriów klas  
 Klasy, które udostępniają różne inne funkcje obejmują:  
  
-   <xref:System.Windows.Forms.ToolStripManager>obsługuje <xref:System.Windows.Forms.ToolStrip>-powiązanych zadań dla całej aplikacji, takie jak scalanie, ustawień i renderowania opcje.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>Umożliwia stosowanie określony styl lub motyw do <xref:System.Windows.Forms.ToolStrip> łatwe.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer>Tworzy pióra i pędzle z tabeli kolorów wymienne (<xref:System.Windows.Forms.ProfessionalColorTable>).  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer>stosuje system kolory i styl płaskim visual <xref:System.Windows.Forms.ToolStrip> aplikacji.  
  
-   <xref:System.Windows.Forms.ToolStripContainer>przypomina <xref:System.Windows.Forms.SplitContainer>. Używa czterech panele zadokowane po stronie (wystąpienia <xref:System.Windows.Forms.ToolStripPanel>) i jeden panelu centralnej (wystąpienia <xref:System.Windows.Forms.ToolStripContentPanel>) do tworzenia typowych rozmieszczenia. Nie można usunąć panele po stronie, ale można je ukryć. Nie można usunąć ani ukryć panel centralnej. Można rozmieścić co najmniej jeden <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, lub <xref:System.Windows.Forms.StatusStrip> formantów w panele po stronie i umożliwia panel centralnej dla innych formantów. <xref:System.Windows.Forms.ToolStripContentPanel> Także sposób uzyskać pomoc techniczną renderowania do treści dla spójny wygląd formularza. <xref:System.Windows.Forms.ToolStripContainer>nie obsługuje interfejsu wielu dokumentów (MDI).  
  
-   <xref:System.Windows.Forms.ToolStripPanel>miejsce do przenoszenia i rozmieszczanie <xref:System.Windows.Forms.ToolStrip> kontrolki. Jeśli tak, można użyć tylko jednego panelu i <xref:System.Windows.Forms.ToolStripPanel> działa dobrze w scenariuszach MDI.  
  
## <a name="see-also"></a>Zobacz też  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip — podsumowanie informacji o technologii](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)  
 [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [MenuStrip, kontrolka](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [StatusStrip, kontrolka](../../../../docs/framework/winforms/controls/statusstrip-control.md)  
 [ContextMenuStrip, kontrolka](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)  
 [BindingNavigator, kontrolka](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
