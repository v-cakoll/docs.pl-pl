---
title: ListView — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: ab2d0d9456f64f215ddbc0003833db1858f0ce1a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569336"
---
# <a name="listview-control-overview-windows-forms"></a>ListView — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.ListView> kontrolka Wyświetla listę elementów z ikonami. Widok listy służy do tworzenia interfejsu użytkownika, takich jak okienku po prawej stronie Eksploratora Windows. Kontrolka ma cztery trybów wyświetlania: LargeIcon, SmallIcon, listy i szczegółów.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co można zrobić za pomocą formantu ListView  
  
> [!NOTE]
>  Tryb wyświetlania dodatkowych, Kafelek, jest dostępna tylko w systemach Windows i systemu operacyjnego Windows Server 2003. Aby uzyskać więcej informacji, zobacz [porady: Włączanie widoku Tile w formancie ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 Wyświetlanie dużych ikon obok tekstu elementu; w trybie LargeIcon elementy są wyświetlane w wielu kolumnach, gdy kontrolka jest wystarczająco duży. Tryb SmallIcon jest taki sam, z tą różnicą, że wyświetla małych ikon. Tryb listy wyświetla małe ikony, ale jest zawsze w jednej kolumnie. Tryb szczegółów wyświetla elementy w wielu kolumnach. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie kolumn do formantu ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md). Tryb widoku jest określany przez <xref:System.Windows.Forms.ListView.View%2A> właściwości. Wszystkie tryby widoku można wyświetlić obrazy z listy obrazów. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie ikon dla kontrolki ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 W poniższej tabeli wymieniono niektóre <xref:System.Windows.Forms.ListView> elementów członkowskich i widoki są prawidłowe w.  
  
|Element członkowski ListView|Widok|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> Właściwość|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> Właściwość|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> — Metoda|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> Właściwość|<xref:System.Windows.Forms.View.Details> lub <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> Zdarzenia|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> — Metoda|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, lub <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> — Metoda|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> — Metoda|<xref:System.Windows.Forms.View.Details> lub <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> Właściwość|Wszystkie widoki, z wyjątkiem <xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> Właściwość|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> Właściwość|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, lub <xref:System.Windows.Forms.View.Tile>|  
  
 Właściwość klucza <xref:System.Windows.Forms.ListView> formant jest <xref:System.Windows.Forms.ListView.Items%2A>, który zawiera elementy wyświetlany przez kontrolkę. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Właściwość zawiera kolekcję elementów aktualnie wybrana w kontrolce. Użytkownik może wybrać wiele elementów, na przykład ich przeciąganie i upuszczanie kilka elementów w czasie innej kontrolce, jeśli <xref:System.Windows.Forms.ListView.MultiSelect%2A> właściwość jest ustawiona na `true`. <xref:System.Windows.Forms.ListView> Formant może wyświetlić pola wyboru obok elementów, jeśli <xref:System.Windows.Forms.ListView.CheckBoxes%2A> właściwość jest ustawiona na `true`.  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> Właściwość określa, jakiego rodzaju akcji użytkownik musi wykonać, aby uaktywnić element na liście: opcje są <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, i <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick> Aktywacja wymaga jednego kliknięcia, aby aktywować elementu. <xref:System.Windows.Forms.ItemActivation.TwoClick> Aktywacja wymaga od użytkownika, kliknij dwukrotnie, aby aktywować elementu; jednym kliknięciem zmienia kolor tekstu elementu. <xref:System.Windows.Forms.ItemActivation.Standard> Aktywacja wymaga od użytkownika, kliknij dwukrotnie, aby uaktywnić element, ale element nie zmienia się wygląd.  
  
 <xref:System.Windows.Forms.ListView> Kontroli obsługuje również stylów wizualnych i inne funkcje, które są dostępne na platformie Windows XP, w tym grupowania, widoku kafelków i wstawiania znaczników. Aby uzyskać więcej informacji, zobacz [funkcje systemu Windows XP i kontrolki formularzy Windows](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Instrukcje: zaznaczanie elementu w kontrolce ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 [Instrukcje: grupowanie elementów w kontrolce ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 [Instrukcje: wyświetlanie znacznika wstawiania w kontrolce ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 [Instrukcje: dodawanie funkcji wyszukiwania do kontrolki ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
