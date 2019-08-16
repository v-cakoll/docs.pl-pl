---
title: 'Instrukcje: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: fd80a6543c83ae957cd9c51b068d0702559f0925
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040272"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Instrukcje: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant
Można ograniczyć lub rozszerzyć polecenia, które użytkownik może wprowadzić, włączając i wyłączając elementy menu w odpowiedzi na działania użytkownika. Elementy menu są domyślnie włączone, gdy są tworzone, ale można je dostosować za pomocą <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości. Tę właściwość można manipulować w czasie projektowania w oknie **Właściwości** lub programowo przez ustawienie jej w kodzie. Aby uzyskać więcej informacji, zobacz [jak: Wyłącz kontrolki ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).

## <a name="to-disable-a-menu-item-at-design-time"></a>Aby wyłączyć element menu w czasie projektowania

1. Z elementem menu wybranym w formularzu Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość na. `false`

    > [!TIP]
    >  Wyłączenie elementu menu pierwszy lub najwyższego poziomu w menu powoduje wyłączenie wszystkich elementów menu zawartych w menu. Analogicznie, wyłączenie elementu menu zawierającego elementy podmenu powoduje wyłączenie elementów podmenu. Jeśli wszystkie polecenia w danym menu są niedostępne dla użytkownika, jest on uznawany za dobry sposób programowania, aby ukryć i wyłączyć całe menu, ponieważ prezentuje to czysty interfejs użytkownika. Należy ukryć i wyłączyć menu, ponieważ ukrywanie samo nie uniemożliwia dostępu do polecenia menu za pośrednictwem klawisza skrótu. Ustaw właściwość elementu menu najwyższego poziomu, aby `false` ukryć całe menu. <xref:System.Windows.Forms.ToolStripItem.Visible%2A>

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Instrukcje: Ukryj kontrolki ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
