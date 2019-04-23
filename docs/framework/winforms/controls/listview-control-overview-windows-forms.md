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
ms.openlocfilehash: a60c415427a1be994f8081725f20e867dca66aa1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101884"
---
# <a name="listview-control-overview-windows-forms"></a>ListView — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.ListView> kontrolka Wyświetla listę elementów z ikonami. Widok listy służy do tworzenia interfejsu użytkownika, takich jak okienku po prawej stronie Eksploratora Windows. Kontrolka ma cztery trybów wyświetlania: LargeIcon, SmallIcon, listy i szczegółów.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co można zrobić za pomocą formantu ListView  
  
> [!NOTE]
>  Tryb wyświetlania dodatkowych, Kafelek, jest dostępna tylko w systemach Windows i systemu operacyjnego Windows Server 2003. Aby uzyskać więcej informacji, zobacz [jak: Włączanie widoku Tile w Windows formantu ListView formularzy](how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 Wyświetlanie dużych ikon obok tekstu elementu; w trybie LargeIcon elementy są wyświetlane w wielu kolumnach, gdy kontrolka jest wystarczająco duży. Tryb SmallIcon jest taki sam, z tą różnicą, że wyświetla małych ikon. Tryb listy wyświetla małe ikony, ale jest zawsze w jednej kolumnie. Tryb szczegółów wyświetla elementy w wielu kolumnach. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kolumn do Windows formantu ListView formularzy](how-to-add-columns-to-the-windows-forms-listview-control.md). Tryb widoku jest określany przez <xref:System.Windows.Forms.ListView.View%2A> właściwości. Wszystkie tryby widoku można wyświetlić obrazy z listy obrazów. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie ikon dla kontrolki ListView formularzy Windows](how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
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
  
 <xref:System.Windows.Forms.ListView> Kontroli obsługuje również stylów wizualnych i inne funkcje, które są dostępne na platformie Windows XP, w tym grupowania, widoku kafelków i wstawiania znaczników.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie ikon dla kontrolki ListView formularzy Windows](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy Windows](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: Wybierz element w kontrolce ListView formularzy Windows](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Instrukcje: Grupowanie elementów w formancie ListView formularzy Windows](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie znacznika wstawiania w formancie ListView formularzy Windows](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie możliwości wyszukiwania do formantu ListView](how-to-add-search-capabilities-to-a-listview-control.md)
- [Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Instrukcje: Tworzenie złożonego interfejsu użytkownika z formularzami Windows](how-to-create-a-multipane-user-interface-with-windows-forms.md)
