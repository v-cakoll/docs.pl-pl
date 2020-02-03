---
title: Grupowanie elementów w kontrolce ListView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736680"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Porady: grupowanie elementów w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant

Funkcja grupowania kontrolki <xref:System.Windows.Forms.ListView> umożliwia wyświetlanie powiązanych zestawów elementów w grupach. Te grupy są rozdzielane na ekranie przez nagłówki grup poziomych, które zawierają tytuły grup. Korzystając z grup <xref:System.Windows.Forms.ListView>, można ułatwić nawigację dużych list, grupując elementy alfabetycznie według daty lub przez inne grupowanie logiczne. Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy:

![Liczby rozdzielone na grupy nieparzyste i parzyste.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.ListView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jeden obiekt <xref:System.Windows.Forms.ListViewGroup> w projektancie lub programowo. Po zdefiniowaniu grupy można przypisać do niej elementy.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Aby dodać lub usunąć grupy w projektancie

1. W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Groups%2A>.

     Zostanie wyświetlony **Edytor kolekcji ListView** .

2. Aby dodać grupę, kliknij przycisk **Dodaj** . Następnie można ustawić właściwości nowej grupy, takie jak <xref:System.Windows.Forms.ListViewGroup.Header%2A> i <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> właściwości. Aby usunąć grupę, zaznacz ją i kliknij przycisk **Usuń** .

## <a name="to-assign-items-to-groups-in-the-designer"></a>Aby przypisać elementy do grup w projektancie

1. W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Items%2A>.

     Zostanie wyświetlony **Edytor kolekcji ListViewItem** .

2. Aby dodać nowy element, kliknij przycisk **Dodaj** . Następnie można ustawić właściwości nowego elementu, takie jak <xref:System.Windows.Forms.ListViewItem.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.

3. Wybierz właściwość <xref:System.Windows.Forms.ListViewItem.Group%2A> i wybierz grupę z listy rozwijanej.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
