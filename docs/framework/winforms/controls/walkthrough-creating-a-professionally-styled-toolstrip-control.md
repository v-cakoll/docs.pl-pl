---
title: 'Przewodnik: tworzenie profesjonalnej kontrolki ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 226e805d0240236899ee0cc290f1060a3b0aa391
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211767"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>Przewodnik: tworzenie profesjonalnej kontrolki ToolStrip

Możesz nadać aplikacji <xref:System.Windows.Forms.ToolStrip> kontroluje profesjonalny wygląd i zachowanie, pisząc własne klasy pochodzącej od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.

W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStrip> formantów, aby utworzyć formant złożony, który przypomina **okienka nawigacji** udostępniane przez Microsoft Outlook®. Następujące zadania są przedstawione w niniejszym przewodniku:

- Tworzenie projektu Biblioteka formantów Windows.

- Projektowanie kontrolki StackView.

- Implementowanie niestandardowego modułu renderowania.

Gdy skończysz, konieczne będzie formantu wielokrotnego niestandardowe klienta za pomocą profesjonalny wygląd kontrolki Microsoft Office® XP.

Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Tworzenie profesjonalnego formantu ToolStrip](how-to-create-a-professionally-styled-toolstrip-control.md).

## <a name="prerequisites"></a>Wymagania wstępne

Visual Studio w celu przeprowadzenia tego instruktażu jest konieczne.

## <a name="create-the-control-library-project"></a>Utwórz projekt Biblioteka formantów

1. W programie Visual Studio Utwórz nowy projekt Biblioteka formantów Windows o nazwie `StackViewLibrary`.

2. W **Eksploratora rozwiązań**, usunąć projekt domyślny formant przez usunięcie pliku źródłowego o nazwie "UserControl1.cs" lub "UserControl1.vb", w zależności od tego, w wybranym języku.

     Aby uzyskać więcej informacji, zobacz [jak: Usuń Delete i wykluczyć elementy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).

3. Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do **StackViewLibrary** projektu. Nazwij nowy plik źródłowy podstawowej z `StackView`.

## <a name="design-the-stackview-control"></a>Projektowanie kontrolki StackView

`StackView` Kontrolka jest kontrolką złożoną z jeden element podrzędny <xref:System.Windows.Forms.ToolStrip> kontroli. Aby uzyskać więcej informacji na temat formanty złożone zobacz [różne typy kontrolek niestandardowych](varieties-of-custom-controls.md).

1. Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStrip> kontrolki na powierzchnię projektową.

2. W **właściwości** oknie <xref:System.Windows.Forms.ToolStrip> właściwości formantu, zgodnie z poniższą tabelą.

    |Właściwość|Wartość|
    |--------------|-----------|
    |Nazwa|`stackStrip`|
    |CanOverflow|`false`|
    |Dock|<xref:System.Windows.Forms.DockStyle.Bottom>|
    |Czcionka|`Tahoma, 10pt, style=Bold`|
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|
    |Dopełnienie|`0, 7, 0, 0`|
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|

3. W programie Windows Forms Designer kliknij <xref:System.Windows.Forms.ToolStrip> kontrolki **Dodaj** przycisku i Dodaj <xref:System.Windows.Forms.ToolStripButton> do `stackStrip` kontroli.

4. W **właściwości** oknie <xref:System.Windows.Forms.ToolStripButton> właściwości formantu, zgodnie z poniższą tabelą.

    |Właściwość|Wartość|
    |--------------|-----------|
    |Nazwa|`mailStackButton`|
    |CheckOnClick|true|
    |Wartość CheckState|<xref:System.Windows.Forms.CheckState.Checked>|
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|
    |ImageTransparentColor|`238, 238, 238`|
    |Margines|`0, 0, 0, 0`|
    |Dopełnienie|`3, 3, 3, 3`|
    |Tekst|**wiadomości e-mail**|
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|

5. Powtórz krok 7 dla trzech <xref:System.Windows.Forms.ToolStripButton> kontrolki.

     Nazwij kontrolki `calendarStackButton`, `contactsStackButton`, i `tasksStackButton`. Ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości **kalendarza**, **kontakty**, i **zadania**, odpowiednio.

## <a name="handle-events"></a>Obsługa zdarzeń

Dwa zdarzenia są ważne dla zapewnienia `StackView` kontroli działają poprawnie. Obsługa <xref:System.Windows.Forms.UserControl.Load> zdarzenie, aby poprawnie położenie formantu. Obsługa <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla każdego <xref:System.Windows.Forms.ToolStripButton> zapewnienie `StackView` kontrolowania zachowania stanu podobny do <xref:System.Windows.Forms.RadioButton> kontroli.

1. W programie Windows Forms Designer wybierz `StackView` kontroli.

2. W **właściwości** okna, kliknij przycisk **zdarzenia**.

3. Kliknij dwukrotnie zdarzenie obciążenia, aby wygenerować `StackView_Load` programu obsługi zdarzeń.

4. W `StackView_Load` procedura obsługi zdarzeń, skopiuj i wklej następujący kod.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]

5. W programie Windows Forms Designer wybierz `mailStackButton` kontroli.

6. W **właściwości** okna, kliknij przycisk **zdarzenia**.

7. Kliknij dwukrotnie zdarzenie Click.

     Windows Forms Designer generuje `mailStackButton_Click` programu obsługi zdarzeń.

8. Zmień nazwę `mailStackButton_Click` procedurę obsługi zdarzeń do `stackButton_Click`.

     Aby uzyskać więcej informacji, zobacz [symbolu kodu Refaktoryzacja zmiany nazwy](/visualstudio/ide/reference/rename).

9. Wstaw następujący kod do `stackButton_Click` programu obsługi zdarzeń.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]

10. W programie Windows Forms Designer wybierz `calendarStackButton` kontroli.

11. W **właściwości** oknie równa zdarzenie Click `stackButton_Click` programu obsługi zdarzeń.

12. Powtórz kroki 10 i 11 dla `contactsStackButton` i `tasksStackButton` kontrolki.

## <a name="define-icons"></a>Zdefiniuj ikon

Każdy `StackView` przycisk ma skojarzona ikona. Dla wygody, każda ikona jest reprezentowany jako ciąg zakodowany w formacie Base64, który jest przeprowadzona przed <xref:System.Drawing.Bitmap> utworzonych na jej podstawie. W środowisku produkcyjnym można przechowywać dane mapy bitowej jako zasób, a ikony są wyświetlane w programie Windows Forms Designer. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie obrazów w tle do formularzy Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).

1. W edytorze kodu, Wstaw następujący kod do `StackView` definicji klasy. Ten kod inicjalizuje bitmap do <xref:System.Windows.Forms.ToolStripButton> ikon.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]

2. Dodaj wywołanie do `InitializeImages` method in Class metoda `StackView` konstruktora klasy.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="implement-a-custom-renderer"></a>Implementowanie niestandardowego modułu renderowania

Można dostosować większość elementów `StackView` kontrolować Moje Implementacja klasy, która pochodzi od klasy <xref:System.Windows.Forms.ToolStripRenderer> klasy. W tej procedurze, zostaną zaimplementowane <xref:System.Windows.Forms.ToolStripProfessionalRenderer> klasę, która dostosowuje uchwytu i rysuje gradientu tła <xref:System.Windows.Forms.ToolStripButton> kontrolki.

1. Wstaw następujący kod do `StackView` kontrolować definicji.

     Jest to definicja `StackRenderer` klasy, co zastępuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, i <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody, aby utworzyć niestandardowy wygląd.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]

2. W `StackView` konstruktora kontrolki, Utwórz nowe wystąpienie klasy `StackRenderer` klasy, a następnie przypisz tego wystąpienia `stackStrip` kontrolki <xref:System.Windows.Forms.ToolStrip.Renderer%2A> właściwości.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="test-the-stackview-control"></a>Testowanie kontrolki StackView

`StackView` Pochodzi od klasy formantu <xref:System.Windows.Forms.UserControl> klasy. W związku z tym, można przetestować kontrolki z **UserControl — kontener testu**. Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

1. Naciśnij klawisz **F5** Aby skompilować projekt i uruchomić **UserControl — kontener testowy**.

2. Przesuń wskaźnik nad przycisków `StackView` sterowania, a następnie kliknij przycisk, aby zobaczyć wygląd stanie wybrania.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu utworzono kontrolkę wielokrotnego niestandardowe klienta profesjonalny wygląd kontrolki Office XP. Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:

- Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>. Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](contextmenu-component-overview-windows-forms.md).

- Tworzenie formularza z automatycznie wypełnione standardowe menu. Aby uzyskać więcej informacji, zobacz [instruktażu: Zapewnianie elementów Menu standardowego dla formularza](walkthrough-providing-standard-menu-items-to-a-form.md).

- Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
- [Instrukcje: Zapewnianie elementów Menu standardowego dla formularza](how-to-provide-standard-menu-items-to-a-form.md)
