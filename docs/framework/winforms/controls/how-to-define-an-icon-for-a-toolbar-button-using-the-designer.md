---
title: 'Instrukcje: określanie ikony dla przycisku ToolBar przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 5de7645ecbf2123df849046a152643cd629b4898
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038234"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Instrukcje: określanie ikony dla przycisku ToolBar przy użyciu narzędzia Projektant

> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ToolBar> do <xref:System.Windows.Forms.ToolBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip>

<xref:System.Windows.Forms.ToolBar>przyciski mogą wyświetlać w nich ikony umożliwiające łatwą identyfikację użytkowników. Jest to realizowane poprzez dodanie obrazów do <xref:System.Windows.Forms.ImageList> składnika i skojarzenie go <xref:System.Windows.Forms.ToolBar> z kontrolką.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ToolBar> formant i <xref:System.Windows.Forms.ImageList> składnik. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).


### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Aby ustawić ikonę dla przycisku paska narzędzi w czasie projektowania

1. Dodaj obrazy do <xref:System.Windows.Forms.ImageList> składnika. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia](how-to-add-or-remove-imagelist-images-with-the-designer.md)Projektant.

2. <xref:System.Windows.Forms.ToolBar> Zaznacz kontrolkę w formularzu.

3. W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.ImageList%2A> właściwość kontrolki na <xref:System.Windows.Forms.ImageList> składnik.

4. ![](./media/visual-studio-ellipsis-button.png)Kliknij właściwość kontrolki,abyjązaznaczyć,anastępniekliknijprzyciskwielokropka(...)woknowłaściwościprogramuVisualStudio.),abyotworzyćEdytorkolekcjiToolBarButton.<xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.Buttons%2A>

5. Użyj przycisku **Dodaj** , aby dodać przyciski do <xref:System.Windows.Forms.ToolBar> kontrolki.

6. W oknie **Właściwości** , które pojawia się w okienku po prawej stronie **edytora kolekcji ToolBarButton** <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> , ustaw właściwość każdego przycisku paska narzędzi na jedną z wartości na liście, która jest rysowana na podstawie obrazów dodanych do <xref:System.Windows.Forms.ImageList> składnik.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolBar>
- [Instrukcje: Zdarzenia menu wyzwalacza dla przycisków paska narzędzi](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar, kontrolka](toolbar-control-windows-forms.md)
- [ImageList, składnik](imagelist-component-windows-forms.md)
