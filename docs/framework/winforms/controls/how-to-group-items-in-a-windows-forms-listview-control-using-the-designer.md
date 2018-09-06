---
title: 'Porady: grupowanie elementów w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 40105ba9ffdc6f61cd9a9e382ba5d2610cbcbca2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749015"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Porady: grupowanie elementów w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant
Funkcja grupowania <xref:System.Windows.Forms.ListView> kontroli pozwala wyświetlić powiązane zestawy elementów w grupach. Te grupy są oddzielone na ekranie nagłówków grup poziomej, zawierające tytułów grup. Możesz użyć <xref:System.Windows.Forms.ListView> grup, aby upewnić się, przechodząc duże listy łatwiejsze przez grupowanie elementów w kolejności alfabetycznej, według daty lub przez inne logiczne grupowanie. Na poniższej ilustracji przedstawiono niektóre zgrupowanych elementów.  
  
 ![Grupy ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ListView> kontroli. Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
 Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jeden <xref:System.Windows.Forms.ListViewGroup> obiektów w Projektancie lub programowo. Po zdefiniowaniu grupy elementów można przypisać do niej.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> grupy są dostępne tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych jakiegokolwiek kodu dotyczące grup nie ma wpływu, a grupy nie będą widoczne. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Aby dodać lub usunąć grupy w Projektancie  
  
1.  W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Groups%2A> właściwości.  
  
     **ListViewGroup — Edytor kolekcji** pojawia się.  
  
2.  Aby dodać grupę, kliknij przycisk **Dodaj** przycisku. Następnie można ustawić właściwości nowej grupy, takie jak <xref:System.Windows.Forms.ListViewGroup.Header%2A> i <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> właściwości. Aby usunąć grupę, wybierz ją, a następnie kliknij przycisk **Usuń** przycisku.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Aby przypisać elementy do grup w Projektancie  
  
1.  W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Items%2A> właściwości.  
  
     **ListViewItem — Edytor kolekcji** pojawia się.  
  
2.  Aby dodać nowy element, kliknij **Dodaj** przycisku. Następnie można ustawić właściwości nowego elementu, takie jak <xref:System.Windows.Forms.ListViewItem.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.  
  
3.  Wybierz <xref:System.Windows.Forms.ListViewItem.Group%2A> właściwości i wybierz grupę z listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Funkcje systemu Windows XP i kontrolek formularzy Windows Forms](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
