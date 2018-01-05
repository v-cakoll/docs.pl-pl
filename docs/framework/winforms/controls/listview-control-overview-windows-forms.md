---
title: "ListView — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bc0f887743e9e129319ca9241203905670334cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="listview-control-overview-windows-forms"></a>ListView — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.ListView> formantu zostanie wyświetlona lista elementy z ikonami. Widok listy służy do tworzenia interfejsu użytkownika, takie jak okienku po prawej stronie Eksploratora Windows. Kontrolka ma cztery trybów wyświetlania: widoku LargeIcon, SmallIcon, listy i szczegółów.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co można zrobić za pomocą formantu ListView  
  
> [!NOTE]
>  Tryb dodatkowe widoku, kafelków, jest dostępna tylko w systemach Windows XP i systemu operacyjnego Windows Server 2003. Aby uzyskać więcej informacji, zobacz [porady: Włączanie widoku Tile w formancie ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 W trybie LargeIcon Wyświetla duże ikony obok tekstu elementu. elementy są wyświetlane w wielu kolumnach, jeśli formant jest wystarczająco duża. W trybie SmallIcon jest taki sam, z wyjątkiem tego, że wyświetla małych ikon. Tryb listy zawiera małe ikony, ale jest zawsze w jednej kolumnie. Tryb szczegółów wyświetla elementy w wielu kolumnach. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie kolumn do formantu ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md). Tryb widoku jest określany przez <xref:System.Windows.Forms.ListView.View%2A> właściwości. Wszystkie tryby widoku można wyświetlić obrazy z listy obrazów. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 W poniższej tabeli wymieniono niektóre <xref:System.Windows.Forms.ListView> elementów członkowskich i widoki są ważne w.  
  
|Element członkowski ListView|Widok|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A>Właściwość|<xref:System.Windows.Forms.View.SmallIcon>lub<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A>Właściwość|<xref:System.Windows.Forms.View.SmallIcon>lub<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>— Metoda|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A>Właściwość|<xref:System.Windows.Forms.View.Details>lub<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem>zdarzenia|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A>— Metoda|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, lub<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A>— Metoda|<xref:System.Windows.Forms.View.SmallIcon>lub<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A>— Metoda|<xref:System.Windows.Forms.View.Details>lub<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A>Właściwość|Wszystkie widoki, z wyjątkiem<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A>Właściwość|<xref:System.Windows.Forms.View.Details>.,|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A>Właściwość|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, lub<xref:System.Windows.Forms.View.Tile>|  
  
 Właściwość klucza <xref:System.Windows.Forms.ListView> formant jest <xref:System.Windows.Forms.ListView.Items%2A>, który zawiera elementy wyświetlany przez formant. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Właściwość zawiera kolekcję elementów aktualnie zaznaczony w formancie. Użytkownik może wybrać wiele elementów, na przykład w celu przeciągnij i upuść kilka elementów jednocześnie do innego formantu, jeśli <xref:System.Windows.Forms.ListView.MultiSelect%2A> właściwość jest ustawiona na `true`. <xref:System.Windows.Forms.ListView> Formant może wyświetlać pola wyboru obok elementów, jeśli <xref:System.Windows.Forms.ListView.CheckBoxes%2A> właściwość jest ustawiona na `true`.  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> Właściwość określa typ akcji użytkownika należy wykonać, aby uaktywnić element na liście: dostępne są następujące opcje <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, i <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick>Aktywacja wymaga jednego kliknięcia, aby aktywować elementu. <xref:System.Windows.Forms.ItemActivation.TwoClick>Aktywacja wymaga od użytkownika kliknij dwukrotnie, aby uaktywnić element; jednym kliknięciem zmienia kolor tekstu elementu. <xref:System.Windows.Forms.ItemActivation.Standard>Aktywacja wymaga od użytkownika kliknij dwukrotnie, aby aktywować elementu, ale element nie zmienia wygląd.  
  
 <xref:System.Windows.Forms.ListView> Formantu obsługuje również style wizualne i inne funkcje, które są dostępne na platformie Windows XP, w tym grupowania, widoku tile i znaczniki wstawiania. Aby uzyskać więcej informacji, zobacz [funkcji systemu Windows XP i formantów formularzy systemu Windows](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).  
  
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
