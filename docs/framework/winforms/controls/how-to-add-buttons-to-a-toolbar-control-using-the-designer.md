---
title: 'Instrukcje: dodawanie przycisków do kontrolki ToolBar przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: e5069dd46a31a65f65a17d750b685d82762e3d11
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038206"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Instrukcje: dodawanie przycisków do kontrolki ToolBar przy użyciu narzędzia Projektant

> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ToolBar> do <xref:System.Windows.Forms.ToolBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip>

Integralną częścią <xref:System.Windows.Forms.ToolBar> kontrolki są przyciski dodawane do niego. Mogą one służyć do zapewnienia łatwego dostępu do poleceń menu lub, Alternatywnie, można umieścić w innym obszarze interfejsu użytkownika aplikacji, aby udostępnić użytkownikom polecenia, które nie są dostępne w strukturze menu.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ToolBar> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).


### <a name="to-add-buttons-at-design-time"></a>Aby dodać przyciski w czasie projektowania

1. <xref:System.Windows.Forms.ToolBar> Zaznacz kontrolkę.

2. W oknie **Właściwości** kliknij <xref:System.Windows.Forms.ToolBar.Buttons%2A> właściwość, aby ją zaznaczyć, a następnie kliknij wielokropek (![przycisk wielokropka (...) w okno Właściwości przycisku programu Visual Studio](./media/visual-studio-ellipsis-button.png).), aby otworzyć element **ToolBarButton Edytor kolekcji**.

3. Za pomocą przycisków **Dodaj** i **Usuń** można dodawać i usuwać <xref:System.Windows.Forms.ToolBar> przyciski z formantu.

4. Skonfiguruj właściwości poszczególnych przycisków w oknie **Właściwości** , które pojawiają się w okienku po prawej stronie edytora. W poniższej tabeli przedstawiono niektóre ważne właściwości, które należy wziąć pod uwagę.

    |Właściwość|Opis|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Ustawia menu, które ma być wyświetlane na przycisku paska narzędzi listy rozwijanej. <xref:System.Windows.Forms.ToolBarButton.Style%2A> Właściwość przycisku paska narzędzi musi być ustawiona na <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>wartość. Ta właściwość przyjmuje wystąpienie <xref:System.Windows.Forms.ContextMenu> klasy jako odwołanie.|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Określa, czy przycisk paska narzędzi stylu przełączania jest częściowo wypychany. <xref:System.Windows.Forms.ToolBarButton.Style%2A> Właściwość przycisku paska narzędzi musi być ustawiona na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>wartość.|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Określa, czy przycisk paska narzędzi stylu przełączania jest obecnie w stanie push. <xref:System.Windows.Forms.ToolBarButton.Style%2A> Właściwość przycisku paska narzędzi musi być ustawiona na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> lub <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Ustawia styl przycisku paska narzędzi. Musi być jedną z wartości w <xref:System.Windows.Forms.ToolBarButtonStyle> wyliczeniu.|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Ciąg tekstowy wyświetlany przez przycisk.|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Tekst wyświetlany jako etykietka narzędzia dla przycisku.|

5. Kliknij przycisk **OK** , aby zamknąć okno dialogowe i utworzyć wybrane panele.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolBar>
- [Instrukcje: Zdefiniuj ikonę dla przycisku paska narzędzi](how-to-define-an-icon-for-a-toolbar-button.md)
- [Instrukcje: Zdarzenia menu wyzwalacza dla przycisków paska narzędzi](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar, kontrolka — omówienie](toolbar-control-overview-windows-forms.md)
- [ToolBar, kontrolka](toolbar-control-windows-forms.md)
