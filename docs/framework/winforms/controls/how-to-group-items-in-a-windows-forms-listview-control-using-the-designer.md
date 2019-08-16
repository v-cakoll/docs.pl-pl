---
title: 'Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039398"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant

Funkcja <xref:System.Windows.Forms.ListView> grupowania kontrolki umożliwia wyświetlanie powiązanych zestawów elementów w grupach. Te grupy są rozdzielane na ekranie przez nagłówki grup poziomych, które zawierają tytuły grup. <xref:System.Windows.Forms.ListView> Grupy umożliwiają łatwiejsze nawigowanie po dużych listach, grupując elementy alfabetycznie według daty lub przez inne grupowanie logiczne. Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy:

![Liczby rozdzielone na grupy nieparzyste i parzyste.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ListView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

Aby włączyć grupowanie, należy najpierw utworzyć jeden lub więcej <xref:System.Windows.Forms.ListViewGroup> obiektów w projektancie lub programowo. Po zdefiniowaniu grupy można przypisać do niej elementy.

> [!NOTE]
> <xref:System.Windows.Forms.ListView>grupy są dostępne tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> gdy aplikacja wywołuje metodę. We wcześniejszych systemach operacyjnych każdy kod dotyczący grup nie ma wpływu, a grupy nie będą wyświetlane. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Aby dodać lub usunąć grupy w projektancie

1. W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio <xref:System.Windows.Forms.ListView.Groups%2A> .](./media/visual-studio-ellipsis-button.png)) obok właściwości.

     Zostanie wyświetlony **Edytor kolekcji ListView** .

2. Aby dodać grupę, kliknij przycisk **Dodaj** . Następnie można ustawić właściwości nowej grupy, takie jak <xref:System.Windows.Forms.ListViewGroup.Header%2A> właściwości i. <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> Aby usunąć grupę, zaznacz ją i kliknij przycisk **Usuń** .

## <a name="to-assign-items-to-groups-in-the-designer"></a>Aby przypisać elementy do grup w projektancie

1. W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio <xref:System.Windows.Forms.ListView.Items%2A> .](./media/visual-studio-ellipsis-button.png)) obok właściwości.

     Zostanie wyświetlony **Edytor kolekcji ListViewItem** .

2. Aby dodać nowy element, kliknij przycisk **Dodaj** . Następnie można ustawić właściwości nowego elementu, <xref:System.Windows.Forms.ListViewItem.Text%2A> na przykład właściwości i. <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>

3. <xref:System.Windows.Forms.ListViewItem.Group%2A> Wybierz właściwość i wybierz grupę z listy rozwijanej.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
