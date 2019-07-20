---
title: ToolStrip — Architektura formantu
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: d0a1441e9bae8d2c1f938e7399c11e736708da4d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363824"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip — Architektura formantu

Klasy <xref:System.Windows.Forms.ToolStrip> i<xref:System.Windows.Forms.ToolStripItem> zapewniają elastyczny, rozszerzalny system do wyświetlania elementów Toolbar, status i menu. Wszystkie te klasy są zawarte w <xref:System.Windows.Forms> przestrzeni nazw i są zwykle nazwane przy użyciu prefiksu "ToolStrip" ( <xref:System.Windows.Forms.ToolStripOverflow>np.) lub z sufiksem "pas <xref:System.Windows.Forms.MenuStrip>" (na przykład).

## <a name="toolstrip"></a>ToolStrip

W poniższych tematach <xref:System.Windows.Forms.ToolStrip> opisano i kontrolki, które pochodzą z tego tematu.

<xref:System.Windows.Forms.ToolStrip>jest abstrakcyjną klasą bazową <xref:System.Windows.Forms.StatusStrip>dla <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, i. Poniższy model obiektów przedstawia <xref:System.Windows.Forms.ToolStrip> hierarchię dziedziczenia.

![Diagram, który pokazuje model obiektów ToolStrip.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)

Dostęp do wszystkich elementów <xref:System.Windows.Forms.ToolStrip> można uzyskać <xref:System.Windows.Forms.ToolStrip.Items%2A> za pomocą kolekcji. Dostęp do wszystkich elementów <xref:System.Windows.Forms.ToolStripDropDownItem> można uzyskać <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> za pomocą kolekcji. W klasie pochodzącej od <xref:System.Windows.Forms.ToolStrip>, można również <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> użyć właściwości, aby uzyskać dostęp tylko do tych elementów, które są aktualnie wyświetlane. Są to elementy, które nie są obecnie w menu przepełnienia.

Następujące elementy zostały zaprojektowane specjalnie w celu bezproblemowego współdziałania <xref:System.Windows.Forms.ToolStripProfessionalRenderer> z <xref:System.Windows.Forms.ToolStripSystemRenderer> i we wszystkich orientacjach. Są one dostępne domyślnie w czasie projektowania dla <xref:System.Windows.Forms.ToolStrip> formantu:

- <xref:System.Windows.Forms.ToolStripButton>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="menustrip"></a>MenuStrip

<xref:System.Windows.Forms.MenuStrip>jest kontenerem najwyższego poziomu, który <xref:System.Windows.Forms.MainMenu>zastępuje. Udostępnia również funkcje obsługi kluczy i interfejsu wielu dokumentów (MDI). Funkcjonalnie <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.MenuStrip>i współdziałanie z, chociaż są one wyprowadzane <xref:System.Windows.Forms.ToolStripItem>z. <xref:System.Windows.Forms.ToolStripDropDownItem>

Następujące elementy zostały zaprojektowane specjalnie w celu bezproblemowego współdziałania <xref:System.Windows.Forms.ToolStripProfessionalRenderer> z <xref:System.Windows.Forms.ToolStripSystemRenderer> i we wszystkich orientacjach. Są one dostępne domyślnie w czasie projektowania dla <xref:System.Windows.Forms.MenuStrip> formantu:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="statusstrip"></a>StatusStrip

<xref:System.Windows.Forms.StatusStrip><xref:System.Windows.Forms.StatusBar> zastępuje formant. Specjalne funkcje programu <xref:System.Windows.Forms.StatusStrip> obejmują niestandardowy układ tabeli, obsługę rozmiarów formularzy i uchwytów przesuwania `Spring` oraz <xref:System.Windows.Forms.ToolStripStatusLabel> właściwość, która umożliwia automatyczne wypełnienie dostępnego miejsca.

Następujące elementy zostały zaprojektowane specjalnie w celu bezproblemowego współdziałania <xref:System.Windows.Forms.ToolStripProfessionalRenderer> z <xref:System.Windows.Forms.ToolStripSystemRenderer> i we wszystkich orientacjach. Są one dostępne domyślnie w czasie projektowania dla <xref:System.Windows.Forms.StatusStrip> formantu:

- <xref:System.Windows.Forms.ToolStripStatusLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripProgressBar>

### <a name="contextmenustrip"></a>ContextMenuStrip

<xref:System.Windows.Forms.ContextMenuStrip>zastępuje <xref:System.Windows.Forms.ContextMenu>. Można skojarzyć <xref:System.Windows.Forms.ContextMenuStrip> z dowolną kontrolką i kliknąć prawym przyciskiem myszy, aby wyświetlić menu kontekstowe (lub menu skrótów). Możesz wyświetlić <xref:System.Windows.Forms.ContextMenuStrip> programowo przy <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> użyciu metody. <xref:System.Windows.Forms.ContextMenuStrip>obsługuje anulowanie <xref:System.Windows.Forms.ToolStripDropDown.Opening> i <xref:System.Windows.Forms.ToolStripDropDown.Closing> zdarzenia umożliwiające obsługę populacji dynamicznej i scenariuszy wielokrotnego kliknięcia. <xref:System.Windows.Forms.ContextMenuStrip>obsługuje obrazy, stan sprawdzania elementu menu, tekst, klucze dostępu, skróty i menu kaskadowe.

Następujące elementy zostały zaprojektowane specjalnie w celu bezproblemowego współdziałania <xref:System.Windows.Forms.ToolStripProfessionalRenderer> z <xref:System.Windows.Forms.ToolStripSystemRenderer> i we wszystkich orientacjach. Są one dostępne domyślnie w czasie projektowania dla <xref:System.Windows.Forms.ContextMenuStrip> formantu:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="toolstrip-generic-features"></a>Funkcje ogólne ToolStrip

W poniższych tematach opisano funkcje i działania, które są ogólne <xref:System.Windows.Forms.ToolStrip> dla formantów pochodnych i.

#### <a name="painting"></a>Płytk

Niestandardowe malowanie w <xref:System.Windows.Forms.ToolStrip> kontrolkach można wykonywać na kilka sposobów. Podobnie jak w przypadku innych kontrolek <xref:System.Windows.Forms.ToolStrip> Windows Forms <xref:System.Windows.Forms.ToolStripItem> , i oba `OnPaint` mają zastąpiły metody i `Paint` zdarzenia. Podobnie jak w przypadku zwykłego malowania, układ współrzędnych jest względny w stosunku do obszaru klienckiego kontrolki; oznacza to, że lewy górny róg kontrolki to 0, 0. Zdarzenie i `OnPaint` Metoda<xref:System.Windows.Forms.ToolStripItem> zachowania przypominają inne zdarzenia farb. `Paint`

Formanty zapewniają również dokładniejszy dostęp do renderowania elementów i kontenerów <xref:System.Windows.Forms.ToolStripRenderer> za pomocą klasy, która ma metody do malowania tła, tła elementu, obrazu elementu, strzałki elementu, tekstu elementu i obramowania <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStrip>. Argumenty zdarzeń dla tych metod uwidaczniają kilka właściwości, takich jak prostokąty, kolory i formaty tekstu, które można dostosować zgodnie z potrzebami.

Aby dostosować zaledwie kilka aspektów sposobu malowania elementu, zwykle zastępujemy <xref:System.Windows.Forms.ToolStripRenderer>.

Jeśli piszesz nowy element i chcesz kontrolować wszystkie aspekty malowania, Zastąp `OnPaint` metodę. W programie `OnPaint`można użyć metod <xref:System.Windows.Forms.ToolStripRenderer>z.

Domyślnie jest to podwójna buforowana funkcja, która <xref:System.Windows.Forms.ToolStrip> korzysta <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> z tego ustawienia.

#### <a name="parenting"></a>Elementy nadrzędne

Koncepcja własności kontenera i elementów nadrzędnych jest bardziej złożona w <xref:System.Windows.Forms.ToolStrip> kontrolkach niż w innych Windows Formsych kontrolkach kontenera. Jest to niezbędne do obsługi scenariuszy dynamicznych, takich jak przepełnienie, udostępnianie elementów listy rozwijanej w wielu <xref:System.Windows.Forms.ToolStrip> elementach i obsługa generacji <xref:System.Windows.Forms.ContextMenuStrip> z formantu.

Poniższa lista zawiera opis elementów członkowskich związanych z elementem nadrzędnym i wyjaśnia ich użycie.

- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>uzyskuje dostęp do elementu, który jest źródłem elementu listy rozwijanej. Jest to podobne do <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, ale zamiast zwracać formant, <xref:System.Windows.Forms.ToolStripItem>zwraca.

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>Określa, który formant jest źródłem <xref:System.Windows.Forms.ContextMenuStrip> , gdy wiele kontrolek ma takie samo. <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>jest akcesorem tylko do <xref:System.Windows.Forms.ToolStripItem.Parent%2A> odczytu właściwości. Element nadrzędny różni się od właściciela w tym elemencie nadrzędnym, który wskazuje zwracaną <xref:System.Windows.Forms.ToolStrip> wartość bieżącą, w której jest wyświetlany element, który może znajdować się w obszarze przepełnienie.

- <xref:System.Windows.Forms.ToolStripItem.Owner%2A>Zwraca element <xref:System.Windows.Forms.ToolStrip> , którego kolekcja elementów zawiera bieżące <xref:System.Windows.Forms.ToolStripItem>. Jest to najlepszy sposób odwołania <xref:System.Windows.Forms.ToolStrip.ImageList%2A> lub innych właściwości na najwyższego poziomu <xref:System.Windows.Forms.ToolStrip> bez pisania specjalnego kodu do obsługi przepełnienia.

#### <a name="behavior-of-inherited-controls"></a>Zachowanie dziedziczonych kontrolek

Następujące kontrolki są blokowane za każdym razem, gdy są używane w dziedziczeniu:

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.ToolStripPanel>obejmuje panele w <xref:System.Windows.Forms.ToolStripContainer> a także poszczególne <xref:System.Windows.Forms.ToolStripPanel> kontrolki.

Na przykład utwórz nową aplikację Windows Forms przy użyciu co najmniej jednej kontrolki z poprzedniej listy. Ustaw modyfikator dostępu co najmniej jednej kontrolki na `public` lub `protected`, a następnie Skompiluj projekt. Dodaj formularz, który dziedziczy po pierwszym formularzu, a następnie wybierz Dziedziczony formant. Formant jest zablokowany, zachowuje się tak, jakby miał `private`modyfikator dostępu.

#### <a name="toolstripcontainer-support-of-inheritance"></a>"ToolStripContainer" — Obsługa dziedziczenia

<xref:System.Windows.Forms.ToolStripContainer> Kontrolka obsługuje ograniczone dziedziczone scenariusze, podobnie jak w poniższym przykładzie:

1. Utwórz nową aplikację Windows Forms.

2. <xref:System.Windows.Forms.ToolStripContainer> Dodaj do formularza.

3. Ustaw modyfikator <xref:System.Windows.Forms.ToolStripContainer> dostępu do `public` lub `protected`.

4. Dodaj dowolną kombinację <xref:System.Windows.Forms.ToolStrip>formantów <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.ContextMenuStrip> do <xref:System.Windows.Forms.ToolStripPanel> regionów <xref:System.Windows.Forms.ToolStripContainer>.

5. Skompiluj projekt.

6. Dodaj formularz, który dziedziczy po pierwszym formularzu.

7. Wybierz dziedziczone <xref:System.Windows.Forms.ToolStripContainer> w formularzu.

#### <a name="inherited-behavior-of-child-controls"></a>Dziedziczone zachowanie formantów podrzędnych

Po wykonaniu poprzednich kroków następuje następujące Odziedziczone zachowanie:

- W projektancie formant pojawia się z dziedziczonym ikoną.

- <xref:System.Windows.Forms.ToolStripPanel> Kontrolki są zablokowane; nie można wybrać ani zmienić rozmieszczenia ich zawartości.

- Można dodać kontrolki do <xref:System.Windows.Forms.ToolStripContentPanel>, przenieść kontrolki i uczynić je kontrolkami <xref:System.Windows.Forms.ToolStripContentPanel>podrzędnymi.

- Zmiany zostaną zachowane po skompilowaniu formularza.

  > [!NOTE]
  > Usuń Modyfikatory dostępu ze wszystkich <xref:System.Windows.Forms.ToolStripPanel> formantów, które są częścią. <xref:System.Windows.Forms.ToolStripContainer> Modyfikator <xref:System.Windows.Forms.ToolStripContainer> dostępu zarządza pełną kontrolką.

#### <a name="partial-trust"></a>Zaufanie częściowe

Ograniczenia dotyczące `ToolStrip`częściowej relacji zaufania są przeznaczone do zapobiegania przypadkowemu wprowadzeniu danych osobowych, które mogą być używane przez osoby nieupoważnione lub usługi. Środki ochronne są następujące:

- `ToolStripDropDown`kontrolki <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> wymagają wyświetlania elementów <xref:System.Windows.Forms.ToolStripControlHost>w. Dotyczy to zarówno formantów wewnętrznych, takich jak <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, jak <xref:System.Windows.Forms.ToolStripProgressBar> i formantów utworzonych przez użytkownika. Jeśli to wymaganie nie jest spełnione, te elementy nie są wyświetlane. Nie zgłoszono żadnego wyjątku.

- Ustawienie właściwości na nie `false` jest dozwolone <xref:System.Windows.Forms.ToolStripDropDown.Closing> , a wartość parametru zdarzenia możliwego do anulowania jest ignorowana. <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> Dzięki temu nie można wprowadzać więcej niż jednego naciśnięcia klawisza bez odrzucania elementu listy rozwijanej. Jeśli to wymaganie nie jest spełnione, takie elementy nie są wyświetlane. Nie zgłoszono żadnego wyjątku.

- Wiele zdarzeń obsługi naciśnięć klawiszy nie zostanie zgłoszonych, jeśli wystąpią w kontekstach częściowego <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>zaufania innego niż.

- Klucze dostępu nie są przetwarzane, <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> gdy nie ma uprawnień.

#### <a name="usage"></a>Użycie

Następujące wzorce użycia mają wpływ na <xref:System.Windows.Forms.ToolStrip> układ, interakcję z klawiaturą oraz zachowanie użytkowników końcowych:

- Przyłączone do<xref:System.Windows.Forms.ToolStripPanel>

  Można zmienić ich położenie <xref:System.Windows.Forms.ToolStripPanel> w obrębie i w <xref:System.Windows.Forms.ToolStripPanel>ciągu s. <xref:System.Windows.Forms.ToolStrip> `false` <xref:System.Windows.Forms.ToolStrip.Stretch%2A> <xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.ToolStrip> Właściwość jest ignorowana, a jeśli właściwość jest, rozmiar zwiększa się w miarę dodawania elementów do. `Dock` <xref:System.Windows.Forms.ToolStrip> Zazwyczaj nie uczestniczy w kolejności tabulacji.

- Zadokowane

  <xref:System.Windows.Forms.ToolStrip> Znajduje się na jednej stronie kontenera w stałej pozycji, a jego rozmiar rozwija się na całej krawędzi, w której jest zadokowany. <xref:System.Windows.Forms.ToolStrip> Zazwyczaj nie uczestniczy w kolejności tabulacji.

- Pozycjonowane absolutnie

  Przypomina inne kontrolki, w których jest umieszczana <xref:System.Windows.Forms.Control.Location%2A> we właściwości, ma stały rozmiar i zazwyczaj uczestniczy w kolejności tabulacji. <xref:System.Windows.Forms.ToolStrip>

#### <a name="keyboard-interaction"></a>Interakcja z klawiaturą

##### <a name="access-keys"></a>Klucze dostępu

W połączeniu z lub za klawiszem ALT klawisze dostępu są jednym ze sposobów uaktywniania kontrolki przy użyciu klawiatury. <xref:System.Windows.Forms.ToolStrip>obsługuje zarówno jawne, jak i niejawne klucze dostępu. Jawna definicja używa znaku handlowego "i" (&) poprzedzającego literę. Niejawna definicja używa algorytmu, który próbuje znaleźć pasujący element na podstawie kolejności znaków w danej `Text` właściwości.

##### <a name="shortcut-keys"></a>Klawisze skrótu

Klawisze skrótu używane przez <xref:System.Windows.Forms.MenuStrip> kombinację <xref:System.Windows.Forms.Keys> wyliczenia (które nie są specyficzne dla kolejności) do definiowania klawisza skrótu. Możesz również użyć <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> właściwości, aby wyświetlić klawisz skrótu tylko z tekstem, taki jak wyświetlanie "del" zamiast "Delete".

##### <a name="navigation"></a>Nawigacja

Klawisz Alt aktywuje <xref:System.Windows.Forms.MenuStrip> wskazywane przez <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. Z tego miejsca Ctrl + Tab nawiguje między <xref:System.Windows.Forms.ToolStrip> kontrolkami `ToolStripPanel`w obrębie. Klawisz TAB i klawisze strzałek na klawiaturze numerycznej Przechodź między elementami w <xref:System.Windows.Forms.ToolStrip>. Specjalny algorytm obsługuje nawigację w regionie przepełnienia. Spacja wybiera <xref:System.Windows.Forms.ToolStripButton>a <xref:System.Windows.Forms.ToolStripDropDownButton>,, <xref:System.Windows.Forms.ToolStripSplitButton>lub.

##### <a name="focus-and-validation"></a>Fokus i walidacja

Gdy jest aktywowany przez klawisz Alt, <xref:System.Windows.Forms.MenuStrip> lub <xref:System.Windows.Forms.ToolStrip> zwykle nie przyjmuje ani nie usuwa fokusu z kontrolki, która aktualnie ma fokus. Jeśli istnieje kontrolka hostowana w obrębie <xref:System.Windows.Forms.MenuStrip> lub listy rozwijanej <xref:System.Windows.Forms.MenuStrip>, formant uzyskuje fokus, gdy użytkownik naciśnie klawisz Tab. Ogólnie <xref:System.Windows.Forms.Control.GotFocus>rzecz biorąc,, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>i <xref:System.Windows.Forms.Control.Leave> zdarzenia<xref:System.Windows.Forms.MenuStrip> nie mogą być wywoływane, gdy są aktywowane przy użyciu klawiatury. W takich przypadkach zamiast tego należy <xref:System.Windows.Forms.MenuStrip.MenuActivate> użyć <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> zdarzeń i.

Domyślnie <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> jest to `false`. Wywołaj <xref:System.Windows.Forms.ContainerControl.Validate%2A> jawnie w formularzu, aby przeprowadzić walidację.

#### <a name="layout"></a>Układ

Układ można <xref:System.Windows.Forms.ToolStrip> kontrolować, wybierając jeden z <xref:System.Windows.Forms.ToolStripLayoutStyle> elementów członkowskich z <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwością.

##### <a name="stack-layouts"></a>Układy stosu

Stacking to rozmieszczenie elementów obok siebie na obu końcach <xref:System.Windows.Forms.ToolStrip>. Poniższa lista zawiera opis układów stosu.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow>jest wartością domyślną. To ustawienie powoduje, <xref:System.Windows.Forms.ToolStrip> że zmiany układu są automatycznie zgodne <xref:System.Windows.Forms.ToolStrip.Orientation%2A> z właściwością do obsługi scenariuszy przeciągania i dokowania.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>Renderuje <xref:System.Windows.Forms.ToolStrip> elementy obok siebie w pionie.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>Renderuje <xref:System.Windows.Forms.ToolStrip> elementy obok siebie w poziomie.

##### <a name="other-features-of-stack-layouts"></a>Inne funkcje układów stosu

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>Określa koniec, <xref:System.Windows.Forms.ToolStrip> do którego element jest wyrównany.

Gdy elementy nie mieszczą się w <xref:System.Windows.Forms.ToolStrip>, pojawia się automatycznie przycisk przepełnienia. Ustawienie <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> właściwości określa, czy element jest wyświetlany w obszarze przeciążenia zawsze, w razie konieczności, czy nigdy.

W zdarzeniu można <xref:System.Windows.Forms.ToolStripItem.Placement%2A> sprawdzić właściwość, aby określić, czy element został umieszczony w głównym <xref:System.Windows.Forms.ToolStrip>, przepełnieniu <xref:System.Windows.Forms.ToolStrip>czy nie jest aktualnie wyświetlany. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> Typowymi przyczynami, dla których element nie jest wyświetlany, jest to, że element nie mieści <xref:System.Windows.Forms.ToolStrip> się na <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> głównym, a jego <xref:System.Windows.Forms.ToolStripItemOverflow.Never>właściwość została ustawiona na.

Zmień element <xref:System.Windows.Forms.ToolStrip> na ruchomy, umieszczając <xref:System.Windows.Forms.ToolStripPanel> go w i <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> ustawiając <xref:System.Windows.Forms.ToolStripGripStyle.Visible>go na.

##### <a name="other-layout-options"></a>Inne opcje układu

Inne opcje układu to <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> i. <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>

##### <a name="flow-layout"></a>Układ przepływu

<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>układ jest wartością domyślną dla <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>i <xref:System.Windows.Forms.ToolStripOverflow>. Jest on podobny do <xref:System.Windows.Forms.FlowLayoutPanel>. Są to następujące <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> funkcje układu:

- Wszystkie funkcje programu <xref:System.Windows.Forms.FlowLayoutPanel> są uwidaczniane <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> przez właściwość. Należy rzutować <xref:System.Windows.Forms.LayoutSettings> klasę <xref:System.Windows.Forms.FlowLayoutSettings> na klasę.

- Możesz użyć <xref:System.Windows.Forms.ToolStripItem.Dock%2A> właściwości i <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> w kodzie, aby wyrównać elementy w wierszu.

- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Właściwość jest ignorowana.

- W zdarzeniu można <xref:System.Windows.Forms.ToolStripItem.Placement%2A> sprawdzić właściwość, aby określić, czy element został umieszczony w głównej <xref:System.Windows.Forms.ToolStrip> czy nie mieści się w nim. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- Uchwyt nie jest renderowany i <xref:System.Windows.Forms.ToolStrip> w związku z tym <xref:System.Windows.Forms.ToolStripPanel> nie <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> można przenieść w stylu układu w elemencie.

- Przycisk przepełnienia nie jest renderowany i <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> jest ignorowany. <xref:System.Windows.Forms.ToolStrip>

##### <a name="table-layout"></a>Układ tabeli

<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>układ jest wartością domyślną dla <xref:System.Windows.Forms.StatusStrip>elementu. Jest on podobny do <xref:System.Windows.Forms.TableLayoutPanel>. Są to następujące <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> funkcje układu:

- Wszystkie funkcje programu <xref:System.Windows.Forms.TableLayoutPanel> są uwidaczniane <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> przez właściwość. Należy rzutować <xref:System.Windows.Forms.LayoutSettings> klasę <xref:System.Windows.Forms.TableLayoutSettings> na klasę.

- Aby wyrównać <xref:System.Windows.Forms.ToolStripItem.Dock%2A> elementy <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> w komórce tabeli, można użyć właściwości i w kodzie.

- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Właściwość jest ignorowana.

- W zdarzeniu można <xref:System.Windows.Forms.ToolStripItem.Placement%2A> sprawdzić właściwość, aby określić, czy element został umieszczony w głównej <xref:System.Windows.Forms.ToolStrip> czy nie mieści się w nim. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- Uchwyt nie jest renderowany i <xref:System.Windows.Forms.ToolStrip> w związku z tym <xref:System.Windows.Forms.ToolStripPanel> nie <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> można przenieść w stylu układu w elemencie.

- Przycisk przepełnienia nie jest renderowany i <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> jest ignorowany. <xref:System.Windows.Forms.ToolStrip>

## <a name="toolstripitem"></a>ToolStripItem

W poniższych tematach <xref:System.Windows.Forms.ToolStripItem> opisano i kontrolki, które pochodzą z tego tematu.

<xref:System.Windows.Forms.ToolStripItem>jest abstrakcyjną klasą bazową dla wszystkich elementów, które przechodzą do <xref:System.Windows.Forms.ToolStrip>. Poniższy model obiektów przedstawia <xref:System.Windows.Forms.ToolStripItem> hierarchię dziedziczenia.

![Diagram, który pokazuje model obiektów ToolStripItem.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)

<xref:System.Windows.Forms.ToolStripItem>klasy dziedziczą bezpośrednio z <xref:System.Windows.Forms.ToolStripItem>lub dziedziczą pośrednio <xref:System.Windows.Forms.ToolStripControlHost> z <xref:System.Windows.Forms.ToolStripItem> lub <xref:System.Windows.Forms.ToolStripDropDownItem>.

<xref:System.Windows.Forms.ToolStripItem>kontrolki muszą być zawarte w <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, lub <xref:System.Windows.Forms.ContextMenuStrip> i nie mogą być dodawane bezpośrednio do formularza. Różne klasy kontenerów zostały zaprojektowane tak, aby zawierały odpowiedni <xref:System.Windows.Forms.ToolStripItem> podzestaw formantów.

W poniższej tabeli wymieniono <xref:System.Windows.Forms.ToolStripItem> elementy sterujące i kontenery, w których wyglądają najlepiej. Mimo że <xref:System.Windows.Forms.ToolStrip> każdy element może być hostowany w <xref:System.Windows.Forms.ToolStrip>kontenerze dowolnego pochodnego, te elementy zostały zaprojektowane tak, aby wyglądały najlepiej w następujących kontenerach:

> [!NOTE]
> <xref:System.Windows.Forms.ToolStripDropDown>nie jest wyświetlany w przyborniku projektanta.

|Zawarty element|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|
|<xref:System.Windows.Forms.ToolStripButton>|Yes|Nie|Nie|Nie|Yes|
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

### <a name="toolstripbutton"></a>Element ToolStripButton

<xref:System.Windows.Forms.ToolStripButton>jest elementem przycisku dla <xref:System.Windows.Forms.ToolStrip>. Można go wyświetlić z różnymi stylami obramowania i można go użyć do reprezentowania i aktywowania Stanów operacyjnych. Możesz również zdefiniować go tak, aby domyślnie miał fokus.

### <a name="toolstriplabel"></a>ToolStripLabel

Funkcja zapewnia funkcje etykiet w <xref:System.Windows.Forms.ToolStrip> kontrolkach. <xref:System.Windows.Forms.ToolStripLabel> Jest to tak samo <xref:System.Windows.Forms.ToolStripButton> , że nie ma fokusu domyślnego i nie jest renderowane jako wypychane lub <xref:System.Windows.Forms.ToolStripLabel> wyróżnione.

<xref:System.Windows.Forms.ToolStripLabel>element hostowany obsługuje klucze dostępu.

<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> Użyjwłaściwości<xref:System.Windows.Forms.ToolStripLabel> ,, i<xref:System.Windows.Forms.ToolStrip>w celu obsługi łącza do formantu w. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>

### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel

<xref:System.Windows.Forms.ToolStripStatusLabel>jest wersją <xref:System.Windows.Forms.ToolStripLabel> zaprojektowaną specjalnie do użytku w <xref:System.Windows.Forms.StatusStrip>programie. Specjalne funkcje obejmują <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>i <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.

### <a name="toolstripseparator"></a>ToolStripSeparator

<xref:System.Windows.Forms.ToolStripSeparator> Powoduje dodanie linii pionowej lub poziomej do paska narzędzi lub menu, w zależności od orientacji. Zawiera grupowanie lub rozróżnienie między elementami, takimi jak te w menu.

Możesz dodać <xref:System.Windows.Forms.ToolStripSeparator> w czasie projektowania, wybierając go z listy rozwijanej. Można jednak również automatycznie utworzyć <xref:System.Windows.Forms.ToolStripSeparator> przez wpisanie łącznika (-) w węźle szablonu projektanta lub <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> w metodzie.

### <a name="toolstripcontrolhost"></a>Elementu ToolStripControlHost

<xref:System.Windows.Forms.ToolStripControlHost>jest abstrakcyjną klasą bazową <xref:System.Windows.Forms.ToolStripTextBox>dla <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripProgressBar>, i. <xref:System.Windows.Forms.ToolStripControlHost>może hostować inne kontrolki, w tym kontrolki niestandardowe, na dwa sposoby:

- Konstruowanie klasy <xref:System.Windows.Forms.Control> zklasą,<xref:System.Windows.Forms.ToolStripControlHost> która pochodzi od. Aby w pełni uzyskać dostęp do hostowanej kontrolki i właściwości, <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> należy rzutować właściwość z powrotem na rzeczywistą klasę, która reprezentuje.

- Rozszerzając <xref:System.Windows.Forms.ToolStripControlHost>i w konstruktorze bez parametrów klasy dziedziczonej Wywołaj konstruktora klasy bazowej przekazującej klasę, która pochodzi od <xref:System.Windows.Forms.Control>. Ta opcja umożliwia Zawijanie wspólnych metod kontroli i właściwości w celu ułatwienia dostępu w <xref:System.Windows.Forms.ToolStrip>programie.

### <a name="toolstripcombobox"></a>ToolStripComboBox

<xref:System.Windows.Forms.ToolStripComboBox>jest zoptymalizowany pod kątem hostingu <xref:System.Windows.Forms.ToolStrip>w. <xref:System.Windows.Forms.ComboBox> Podzestaw właściwości i zdarzeń kontrolki hostowanej jest widoczny na <xref:System.Windows.Forms.ToolStripComboBox> poziomie, ale kontrola podstawowa <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> jest w pełni dostępna za pomocą właściwości.

### <a name="toolstriptextbox"></a>ToolStripTextBox

<xref:System.Windows.Forms.ToolStripTextBox>jest zoptymalizowany pod kątem hostingu <xref:System.Windows.Forms.ToolStrip>w. <xref:System.Windows.Forms.TextBox> Podzestaw właściwości i zdarzeń kontrolki hostowanej jest widoczny na <xref:System.Windows.Forms.ToolStripTextBox> poziomie, ale kontrola podstawowa <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> jest w pełni dostępna za pomocą właściwości.

### <a name="toolstripprogressbar"></a>ToolStripProgressBar

<xref:System.Windows.Forms.ToolStripProgressBar>jest zoptymalizowany pod kątem hostingu <xref:System.Windows.Forms.ToolStrip>w. <xref:System.Windows.Forms.ProgressBar> Podzestaw właściwości i zdarzeń kontrolki hostowanej jest widoczny na <xref:System.Windows.Forms.ToolStripProgressBar> poziomie, ale kontrola podstawowa <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> jest w pełni dostępna za pomocą właściwości.

### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem

<xref:System.Windows.Forms.ToolStripDropDownItem>jest abstrakcyjną klasą bazową <xref:System.Windows.Forms.ToolStripDropDownButton>dla <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripSplitButton>i, która może hostować elementy bezpośrednio lub hostować dodatkowe elementy w kontenerze rozwijanym. W tym <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> <xref:System.Windows.Forms.ToolStrip.Items%2A> celu należy ustawić właściwość na <xref:System.Windows.Forms.ToolStripDropDown> iustawićwłaściwość.<xref:System.Windows.Forms.ToolStripDropDown> Uzyskuj dostęp do tych elementów listy rozwijanej bezpośrednio <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> przez właściwość.

### <a name="toolstripmenuitem"></a>ToolStripMenuItem

<xref:System.Windows.Forms.ToolStripMenuItem>jest to <xref:System.Windows.Forms.ToolStripDropDownMenu> <xref:System.Windows.Forms.ContextMenuStrip> , że działa z i, aby obsłużyć specjalne wyróżnianie, układ i układ kolumn dla menu. <xref:System.Windows.Forms.ToolStripDropDownItem>

### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton

<xref:System.Windows.Forms.ToolStripDropDownButton>Wygląda na to, ale wyświetla obszar rozwijany, gdy użytkownik go klika. <xref:System.Windows.Forms.ToolStripButton> Ukryj lub Pokaż strzałkę listy rozwijanej, ustawiając <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> właściwość. <xref:System.Windows.Forms.ToolStripDropDownButton><xref:System.Windows.Forms.ToolStrip>hosty ,którewyświetlaelementy,które<xref:System.Windows.Forms.ToolStripOverflowButton> przepełnią.

### <a name="toolstripsplitbutton"></a>ToolStripSplitButton

<xref:System.Windows.Forms.ToolStripSplitButton>łączy funkcje przycisku i listy rozwijanej.

Użyj właściwości <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> , aby <xref:System.Windows.Forms.Control.Click> zsynchronizować zdarzenie wybranego elementu listy rozwijanej z elementem wyświetlanym na przycisku.

### <a name="toolstripitem-generic-features"></a>Funkcje ogólne ToolStripItem

<xref:System.Windows.Forms.ToolStripItem>udostępnia następujące funkcje ogólne i opcje do dziedziczenia formantów:

- Zdarzenia podstawowe

- Obsługa obrazów

- Wyrównanie

- Relacja tekstu i obrazu

- Styl wyświetlania

#### <a name="core-events"></a>Zdarzenia podstawowe

<xref:System.Windows.Forms.ToolStripItem>kontrolki odbierają własne zdarzenia klikania, myszy i malowania oraz mogą wykonywać pewne czynności przed przetworzeniem klawiatury.

#### <a name="image-handling"></a>Obsługa obrazów

<xref:System.Windows.Forms.ToolStripItem.Image%2A>Właściwości, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, ,<xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A> iodnosząsię<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> do różnych aspektów obsługi obrazu. <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A> Używaj obrazów w <xref:System.Windows.Forms.ToolStrip> kontrolkach przez ustawienie tych właściwości bezpośrednio lub przez ustawienie właściwości tylko <xref:System.Windows.Forms.ToolStrip.ImageList%2A> w czasie wykonywania.

Skalowanie obrazów jest określane przez interakcję właściwości w obu <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripItem>, w następujący sposób:

- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>to skala obrazu końcowego określona przez kombinację <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> ustawienia obrazu i <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> ustawienia kontenera.

  - Jeśli <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> <xref:System.Windows.Forms.ToolStripItemImageScaling> jest `true` (wartość domyślna) i jest <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, nie ma żadnego skalowania obrazu, <xref:System.Windows.Forms.ToolStrip> a rozmiar jest większy niż największy element lub określony minimalny rozmiar.

  - Jeśli <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> jest `false` i jest<xref:System.Windows.Forms.ToolStripItemImageScaling> <xref:System.Windows.Forms.ToolStrip> , nie występuje ani obraz, ani skalowanie. <xref:System.Windows.Forms.ToolStripItemImageScaling.None>

#### <a name="alignment"></a>Wyrównanie

Wartość <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwości określa koniec <xref:System.Windows.Forms.ToolStrip> elementu, w którym jest wyświetlany element. Właściwość działa tylko wtedy, gdy styl <xref:System.Windows.Forms.ToolStrip> układu jest ustawiony na jedną z wartości przepełnienia stosu. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>

Elementy są umieszczane <xref:System.Windows.Forms.ToolStrip> w w kolejności, w jakiej elementy są wyświetlane w kolekcji Items. Aby programowo zmienić lokalizację elementu, użyj <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> metody w celu przeniesienia elementu w kolekcji. Ta metoda przenosi element, ale nie duplikuje go.

#### <a name="text-and-image-relationship"></a>Relacja tekstu i obrazu

Właściwość definiuje względne położenie obrazu w odniesieniu do tekstu <xref:System.Windows.Forms.ToolStripItem>na. <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Elementy, które nie mają obrazu, tekstu lub obu obydwu są traktowane jako specjalne przypadki, <xref:System.Windows.Forms.ToolStripItem> aby nie wyświetlały pustego miejsca dla brakującego elementu lub elementów.

#### <a name="display-style"></a>Styl wyświetlania

<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>umożliwia ustawienie wartości tekstu i właściwości obrazu elementu, jednocześnie wyświetlając tylko to, czego potrzebujesz. Jest to zwykle używane do zmiany tylko stylu wyświetlania podczas wyświetlania tego samego elementu w innym kontekście.

## <a name="accessory-classes"></a>Klasy akcesoriów

Klasy, które udostępniają różne inne funkcje, obejmują:

- <xref:System.Windows.Forms.ToolStripManager>obsługuje <xref:System.Windows.Forms.ToolStrip>zadania związane z całymi aplikacjami, takie jak scalanie, ustawienia i opcje modułu renderowania.

- <xref:System.Windows.Forms.ToolStripRenderer>umożliwia <xref:System.Windows.Forms.ToolStrip> łatwe stosowanie określonego stylu lub motywu.

- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>tworzy pióra i pędzle na podstawie zastosowanej tabeli kolorów<xref:System.Windows.Forms.ProfessionalColorTable>().

- <xref:System.Windows.Forms.ToolStripSystemRenderer>stosuje kolory systemowe i płaski styl wizualizacji do <xref:System.Windows.Forms.ToolStrip> aplikacji.

- <xref:System.Windows.Forms.ToolStripContainer>jest podobny do <xref:System.Windows.Forms.SplitContainer>. Stosuje cztery zadokowane panele boczne (wystąpienia <xref:System.Windows.Forms.ToolStripPanel>) i jeden centralny Panel (wystąpienie programu <xref:System.Windows.Forms.ToolStripContentPanel>), aby utworzyć typowe rozwiązanie. Paneli boczne nie można usunąć, ale można je ukryć. Nie można usunąć ani ukryć środkowego panelu. Można rozmieścić jeden lub więcej <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.StatusStrip> kontrolek w panelach bocznych, a także użyć środkowego panelu dla innych kontrolek. Zapewnia <xref:System.Windows.Forms.ToolStripContentPanel> również sposób uzyskania obsługi modułu renderowania w treści formularza pod kątem spójnego wyglądu. <xref:System.Windows.Forms.ToolStripContainer>nie obsługuje interfejsu wielu dokumentów (MDI).

- <xref:System.Windows.Forms.ToolStripPanel>zapewnia miejsce do przesuwania i <xref:System.Windows.Forms.ToolStrip> rozmieszczania kontrolek. Możesz użyć tylko jednego panelu, jeśli tak się stanie, i <xref:System.Windows.Forms.ToolStripPanel> dobrze działa w scenariuszach interfejsu MDI.

## <a name="see-also"></a>Zobacz także

- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md)
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
- [MenuStrip, kontrolka](menustrip-control-windows-forms.md)
- [StatusStrip, kontrolka](statusstrip-control.md)
- [ContextMenuStrip, kontrolka](contextmenustrip-control.md)
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
