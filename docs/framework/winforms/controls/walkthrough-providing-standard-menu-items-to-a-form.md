---
title: 'Przewodnik: zapewnianie elementów menu standardowego dla formularza'
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
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211489"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Przewodnik: zapewnianie elementów menu standardowego dla formularza

Możesz podać standardowe menu formularzy przy użyciu <xref:System.Windows.Forms.MenuStrip> kontroli.

W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.MenuStrip> formantu, aby utworzyć standardowe menu. Formularz również reaguje, gdy użytkownik wybierze element menu. Następujące zadania są przedstawione w niniejszym przewodniku:

- Tworzenie projektu Windows Forms.

- Tworzenie standardowego menu.

- Tworzenie <xref:System.Windows.Forms.StatusStrip> kontroli.

- Obsługa wyboru elementu menu.

Po zakończeniu będziesz mieć formularza przy użyciu standardowego menu, które wyświetla zaznaczenia elementów menu w <xref:System.Windows.Forms.StatusStrip> kontroli.

Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Zapewnianie elementów Menu standardowego dla formularza](how-to-provide-standard-menu-items-to-a-form.md).

## <a name="prerequisites"></a>Wymagania wstępne

Visual Studio w celu przeprowadzenia tego instruktażu jest konieczne.

## <a name="create-the-project"></a>Utwórz projekt

1. W programie Visual Studio Utwórz projekt aplikacji Windows o nazwie **StandardMenuForm** (**pliku** > **New** > **projektu**   >  **Visual C#**  lub **języka Visual Basic** > **Classic Desktop**  >  **Windows Forms aplikacji**).

2. W programie Windows Forms Designer wybierz formularz.

## <a name="create-a-standard-menu"></a>Utwórz standardowe menu

Windows Forms Designer może automatycznie wypełnić <xref:System.Windows.Forms.MenuStrip> kontrolki z elementów menu standardowego.

1. Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formantu do formularza.

2. Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> symbol tagu inteligentnego kontrolki (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Wstaw elementy standardowe**.

     <xref:System.Windows.Forms.MenuStrip> Kontrolka zostanie wypełniona elementów menu standardowego.

3. Kliknij przycisk **pliku** element menu, aby zobaczyć jego elementy menu domyślne i odpowiadające im ikony.

## <a name="create-a-statusstrip-control"></a>Utwórz StatusStrip, kontrolka

Użyj <xref:System.Windows.Forms.StatusStrip> formantu, aby wyświetlić stan dla aplikacji Windows Forms. W bieżącym przykładzie wybrane przez użytkownika elementy menu są wyświetlane w <xref:System.Windows.Forms.StatusStrip> kontroli.

1. Z **przybornika**, przeciągnij <xref:System.Windows.Forms.StatusStrip> formantu do formularza.

     <xref:System.Windows.Forms.StatusStrip> Kontroli automatycznie dokowane do dolnej części formularza.

2. Kliknij przycisk <xref:System.Windows.Forms.StatusStrip> przycisk listy rozwijanej i wybierz formantu **StatusLabel** dodać <xref:System.Windows.Forms.ToolStripStatusLabel> kontrolę <xref:System.Windows.Forms.StatusStrip> kontroli.

## <a name="handle-item-selection"></a>Wybór elementu uchwytu

Obsługa <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzenie, aby odpowiadać, gdy użytkownik wybierze element menu.

1. Kliknij przycisk **pliku** elementu menu, który został utworzony w tworzenie sekcji standardowe Menu.

2. W **właściwości** okna, kliknij przycisk **zdarzenia**.

3. Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.

     Windows Forms Designer generuje moduł obsługi zdarzenia <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.

4. Wstaw następujący kod do obsługi zdarzeń.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. Wstaw `UpdateStatus` definicję metody narzędzie do formularza.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>Punkt kontrolny — testowanie formularza

1. Naciśnij klawisz **F5** Aby skompilować i uruchomić formularz.

2. Kliknij przycisk **pliku** element menu, aby otworzyć menu.

3. Na **pliku** menu, kliknij jeden z elementów, aby go zaznaczyć.

     <xref:System.Windows.Forms.StatusStrip> Kontrolka Wyświetla wybrany element.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu utworzono formularza standardowe menu. Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:

- Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>. Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](contextmenu-component-overview-windows-forms.md).

- Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

- Nadaj swojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki. Aby uzyskać więcej informacji, zobacz [jak: Ustawienie modułu renderowania ToolStrip dla aplikacji](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip, kontrolka](menustrip-control-windows-forms.md)
