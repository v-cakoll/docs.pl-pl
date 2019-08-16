---
title: 'Instrukcje: przenoszenie ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039794"
---
# <a name="how-to-move-toolstripmenuitems"></a>Instrukcje: przenoszenie ToolStripMenuItems
W czasie projektowania można przenieść całe menu najwyższego poziomu i ich elementy menu do innego miejsca na <xref:System.Windows.Forms.MenuStrip>. Można również przenosić poszczególne elementy menu między menu najwyższego poziomu lub zmieniać pozycję elementów menu w menu.

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Aby przenieść menu najwyższego poziomu i jego elementy menu do innej lokalizacji najwyższego poziomu

1. Kliknij i przytrzymaj lewy przycisk myszy w menu, które chcesz przenieść.

2. Przeciągnij punkt wstawiania do menu najwyższego poziomu, które jest przed zamierzoną nową lokalizacją i zwolnij lewy przycisk myszy.

     Wybrane menu przenosi się na prawo od punktu wstawiania.

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Aby przenieść menu najwyższego poziomu i jego elementy menu do lokalizacji rozwijanej

1. Kliknij prawym przyciskiem myszy menu, które chcesz przenieść, a następnie naciśnij klawisze CTRL + X lub kliknij menu, a następnie wybierz polecenie Wytnij z menu skrótów.

2. W docelowym menu najwyższego poziomu kliknij lewym przyciskiem myszy element menu powyżej zamierzonej nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem element menu powyżej zamierzonej nowej lokalizacji i wybierz polecenie **Wklej** z menu skrótów.

     Wycięte menu jest wstawiane po wybranym elemencie menu.

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Aby przenieść element menu w menu przy użyciu edytora kolekcji Items

1. Kliknij prawym przyciskiem myszy menu, które zawiera element menu, który chcesz przenieść.

2. Z menu skrótów wybierz polecenie **Edytuj DropDownItems**.

3. W **edytorze kolekcji elementów**kliknij lewym przyciskiem myszy element menu, który chcesz przenieść.

4. Kliknij klawisze strzałek w górę i w dół, aby przenieść element menu w menu.

5. Kliknij przycisk **OK**.

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Aby przenieść element menu w menu przy użyciu klawiatury

1. Naciśnij i przytrzymaj klawisz ALT.

2. Kliknij i przytrzymaj lewym przyciskiem myszy element menu, który chcesz przenieść.

3. Przeciągnij element menu do nowej lokalizacji i zwolnij lewym przyciskiem myszy.

## <a name="to-move-a-menu-item-to-another-menu"></a>Aby przenieść element menu do innego menu

1. Kliknij lewym przyciskiem myszy element menu, który chcesz przenieść, a następnie naciśnij klawisze CTRL + X lub kliknij prawym przyciskiem myszy element menu, a następnie wybierz polecenie Wytnij z menu skrótów.

2. Kliknij menu po lewej stronie, które będzie zawierać wycięte elementy menu.

3. Kliknij prawym przyciskiem myszy element menu, który jest przed zamierzoną nową lokalizacją, a następnie naciśnij klawisze CTRL + V lub kliknij element menu znajdujący się przed zamierzoną nową lokalizacją i wybierz polecenie **Wklej** z menu skrótów.

     Wycięty element menu jest wstawiany po wybranym elemencie menu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
