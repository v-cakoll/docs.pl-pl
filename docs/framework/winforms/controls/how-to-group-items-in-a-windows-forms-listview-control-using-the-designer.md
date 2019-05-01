---
title: 'Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 7c25c012798adcf90c652beb91a7550406e5f8ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013390"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant
Funkcja grupowania <xref:System.Windows.Forms.ListView> kontroli pozwala wyświetlić powiązane zestawy elementów w grupach. Te grupy są oddzielone na ekranie nagłówków grup poziomej, zawierające tytułów grup. Możesz użyć <xref:System.Windows.Forms.ListView> grup, aby upewnić się, przechodząc duże listy łatwiejsze przez grupowanie elementów w kolejności alfabetycznej, według daty lub przez inne logiczne grupowanie. Na poniższej ilustracji przedstawiono niektóre zgrupowanych elementów.  
  
 ![Grupy ListView](./media/listviewgroups.gif "ListViewGroups")  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ListView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
 Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jeden <xref:System.Windows.Forms.ListViewGroup> obiektów w Projektancie lub programowo. Po zdefiniowaniu grupy elementów można przypisać do niej.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> grupy są dostępne tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych jakiegokolwiek kodu dotyczące grup nie ma wpływu, a grupy nie będą widoczne. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Aby dodać lub usunąć grupy w Projektancie  
  
1. W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Groups%2A> właściwości.  
  
     **ListViewGroup — Edytor kolekcji** pojawia się.  
  
2. Aby dodać grupę, kliknij przycisk **Dodaj** przycisku. Następnie można ustawić właściwości nowej grupy, takie jak <xref:System.Windows.Forms.ListViewGroup.Header%2A> i <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> właściwości. Aby usunąć grupę, wybierz ją, a następnie kliknij przycisk **Usuń** przycisku.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Aby przypisać elementy do grup w Projektancie  
  
1. W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Items%2A> właściwości.  
  
     **ListViewItem — Edytor kolekcji** pojawia się.  
  
2. Aby dodać nowy element, kliknij **Dodaj** przycisku. Następnie można ustawić właściwości nowego elementu, takie jak <xref:System.Windows.Forms.ListViewItem.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.  
  
3. Wybierz <xref:System.Windows.Forms.ListViewItem.Group%2A> właściwości i wybierz grupę z listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
