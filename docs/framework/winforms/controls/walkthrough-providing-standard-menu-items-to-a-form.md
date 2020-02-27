---
title: 'Wskazówki: zapewnianie elementów menu standardowego dla formularza'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628777"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Wskazówki: zapewnianie elementów menu standardowego dla formularza

Możesz dostarczyć menu standardowe dla formularzy z kontrolką <xref:System.Windows.Forms.MenuStrip>.

W tym instruktażu pokazano, jak za pomocą formantu <xref:System.Windows.Forms.MenuStrip> utworzyć standardowy menu. Formularz również reaguje, gdy użytkownik wybierze element menu. W tym instruktażu przedstawiono następujące zadania:

- Tworzenie projektu Windows Forms.

- Tworzenie standardowego menu.

- Tworzenie kontrolki <xref:System.Windows.Forms.StatusStrip>.

- Obsługa wyboru elementu menu.

Gdy skończysz, będziesz mieć formularz z menu standardowym, w którym wyświetlane są wybrane elementy menu w kontrolce <xref:System.Windows.Forms.StatusStrip>.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: zapewnianie elementów menu standardowego w formularzu](how-to-provide-standard-menu-items-to-a-form.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.

## <a name="create-the-project"></a>Tworzenie projektu

1. W programie Visual Studio Utwórz projekt aplikacji systemu Windows o **nazwie StandardMenuForm** (**plik** > **New** > **Project** > **Visual C#**  lub **Visual Basic** > **klasycznego pulpitu** > Windows Forms **aplikacji**).

2. W Projektant formularzy systemu Windows wybierz formularz.

## <a name="create-a-standard-menu"></a>Tworzenie menu standardowego

Projektant formularzy systemu Windows może automatycznie wypełnić formant <xref:System.Windows.Forms.MenuStrip> za pomocą standardowych elementów menu.

1. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.MenuStrip> na formularz.

2. Kliknij symbol akcji projektanta <xref:System.Windows.Forms.MenuStrip> kontrolki (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) i wybierz pozycję **Wstaw elementy standardowe**.

     Formant <xref:System.Windows.Forms.MenuStrip> zostanie wypełniony elementami menu Standard.

3. Kliknij element menu **plik** , aby wyświetlić jego domyślne elementy menu i odpowiadające im ikony.

## <a name="create-a-statusstrip-control"></a>Tworzenie kontrolki StatusStrip

Użyj kontrolki <xref:System.Windows.Forms.StatusStrip>, aby wyświetlić stan aplikacji Windows Forms. W bieżącym przykładzie elementy menu wybrane przez użytkownika są wyświetlane w kontrolce <xref:System.Windows.Forms.StatusStrip>.

1. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.StatusStrip> na formularz.

     Formant <xref:System.Windows.Forms.StatusStrip> automatycznie zadokuje w dolnej części formularza.

2. Kliknij przycisk listy rozwijanej <xref:System.Windows.Forms.StatusStrip> kontrolki i wybierz pozycję **StatusLabel** , aby dodać kontrolkę <xref:System.Windows.Forms.ToolStripStatusLabel> do kontrolki <xref:System.Windows.Forms.StatusStrip>.

## <a name="handle-item-selection"></a>Obsługuj zaznaczenie elementu

Obsługuj zdarzenie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>, aby odpowiedzieć, gdy użytkownik wybierze element menu.

1. Kliknij element menu **plik** , który został utworzony w sekcji Tworzenie standardowego menu.

2. W oknie **Właściwości** kliknij pozycję **zdarzenia**.

3. Kliknij dwukrotnie zdarzenie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.

     Projektant formularzy systemu Windows generuje procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.

4. Wstaw następujący kod do programu obsługi zdarzeń.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. Wstaw definicję metody `UpdateStatus` narzędzia do formularza.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>Punkt kontrolny — testowanie formularza

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić formularz.

2. Kliknij element menu **plik** , aby otworzyć menu.

3. W menu **plik** kliknij jeden z elementów, aby go zaznaczyć.

     Kontrolka <xref:System.Windows.Forms.StatusStrip> Wyświetla wybrany element.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu utworzono formularz z menu standardowym. W wielu innych celach można użyć <xref:System.Windows.Forms.ToolStrip>ej rodziny formantów:

- Utwórz menu skrótów dla kontrolek z <xref:System.Windows.Forms.ContextMenuStrip>. Aby uzyskać więcej informacji, zobacz temat [Omówienie składnika](contextmenu-component-overview-windows-forms.md)usługi.

- Utwórz formularz interfejsu wielu dokumentów (MDI) z kontrolkami <xref:System.Windows.Forms.ToolStrip> dokowania. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie formularza MDI za pomocą scalania menu i formantów ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

- Nadaj <xref:System.Windows.Forms.ToolStrip> kontrolę nad profesjonalnym wyglądem. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie modułu renderowania ToolStrip dla aplikacji](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip, kontrolka](menustrip-control-windows-forms.md)
