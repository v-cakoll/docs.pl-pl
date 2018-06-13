---
title: 'Porady: grupowanie elementów w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: c532cadc5b42c26f1598c4e7586309cf690456bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539345"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Porady: grupowanie elementów w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant
Funkcji grupowania <xref:System.Windows.Forms.ListView> kontroli umożliwia wyświetlanie zestawów powiązanych elementów w grupach. Grupy te są oddzielone na ekranie nagłówki poziomy grupy, które zawierają tytuły grupy. Można użyć <xref:System.Windows.Forms.ListView> grupy, aby łatwiej nawigowanie po dużych list przez alfabetycznie, grupowanie elementów według daty lub logiczne grupowanie. Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy.  
  
 ![Widok listy grup](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ListView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
 Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jeden <xref:System.Windows.Forms.ListViewGroup> obiektów w Projektancie lub programowo. Po zdefiniowaniu grupy elementów można przypisać do niej.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> grupy są dostępne tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] podczas wywołania aplikacji <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych dowolny kod odnoszących się do grupy nie ma wpływu i grup nie będą wyświetlane. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Aby dodać lub usunąć grupy w Projektancie  
  
1.  W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Groups%2A> właściwości.  
  
     **Edytora kolekcji ListViewGroup** pojawi się.  
  
2.  Aby dodać grupę, kliknij przycisk **Dodaj** przycisku. Następnie można ustawić właściwości nowej grupy, takie jak <xref:System.Windows.Forms.ListViewGroup.Header%2A> i <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> właściwości. Aby usunąć grupę, zaznacz go i kliknij przycisk **Usuń** przycisku.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Aby przypisać elementy w grupach w Projektancie  
  
1.  W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Items%2A> właściwości.  
  
     **Edytora kolekcji ListViewItem** pojawi się.  
  
2.  Aby dodać nowy element, kliknij przycisk **Dodaj** przycisku. Następnie można ustawić właściwości nowy element, taki jak <xref:System.Windows.Forms.ListViewItem.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.  
  
3.  Wybierz <xref:System.Windows.Forms.ListViewItem.Group%2A> właściwości i wybierz grupę z listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Funkcje systemu Windows XP i formantów formularzy systemu Windows](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
