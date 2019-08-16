---
title: 'Instrukcje: ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 968d34a5f79d469ef62beaa8ac96742d73391b22
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039743"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Instrukcje: ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant
Ukrywanie elementów menu to sposób sterowania interfejsem użytkownika aplikacji i ograniczania poleceń użytkownika. Często warto ukryć całe menu, gdy wszystkie elementy menu są niedostępne. Spowoduje to zmniejszenie liczby odniesień użytkownika. Ponadto możesz chcieć ukryć i wyłączyć menu lub element menu, ponieważ samo ukrywanie nie uniemożliwia użytkownikowi uzyskania dostępu do polecenia menu przy użyciu klawisza skrótu. Aby uzyskać więcej informacji na temat wyłączania [elementów menu, zobacz How to: Wyłącz kontrolki ToolStripMenuItems przy użyciu narzędzia](how-to-disable-toolstripmenuitems-using-the-designer.md)Projektant.

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>Aby ukryć menu najwyższego poziomu i jego elementy podmenu

1. Wybierz element menu najwyższego poziomu i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Visible%2A> Właściwość <xref:System.Windows.Forms.ToolStripItem.Available%2A> or na `false`.

     Ukrycie elementu menu najwyższego poziomu spowoduje również ukrycie wszystkich elementów menu w tym menu. Jeśli klikniesz pozycję inna niż w przypadku <xref:System.Windows.Forms.MenuStrip> `false`ustawienia <xref:System.Windows.Forms.ToolStripItem.Visible%2A> na, cały element menu najwyższego poziomu i jego elementy podmenu znikną z formularza, w ten sposób pokazujesz efekt czasu wykonywania akcji. Aby wyświetlić ukryty element menu najwyższego poziomu w czasie projektowania, kliknij na <xref:System.Windows.Forms.MenuStrip> pasku **składnika**, w menu **Konspekt dokumentu**lub u góry siatki właściwości.

> [!NOTE]
>  W scenariuszu scalania nie będzie rzadko ukrywane całe menu poza menu podrzędnym wielu dokumentów (MDI).

## <a name="to-hide-a-submenu-item"></a>Aby ukryć element podmenu

1. Wybierz element podmenu i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość na. `false`

     Ukrycie elementu podmenu pozostanie widoczny w formularzu w czasie projektowania, aby można było łatwo wybrać go do dalszej pracy. Będzie ona faktycznie ukryta w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
- [Instrukcje: Wyłączanie kontrolki ToolStripMenuItems przy użyciu narzędzia Projektant](how-to-disable-toolstripmenuitems-using-the-designer.md)
