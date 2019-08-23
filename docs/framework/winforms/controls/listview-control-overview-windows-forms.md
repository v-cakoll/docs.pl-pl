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
ms.openlocfilehash: 7b7eac942a7e857ad731c0f77389e84aee287c08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952164"
---
# <a name="listview-control-overview-windows-forms"></a>ListView — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms wyświetla listę elementów z ikonami. Widok listy służy do tworzenia interfejsu użytkownika, takiego jak prawy panel Eksploratora Windows. Kontrolka ma cztery tryby wyświetlania: Widoku LargeIcon, SmallIcon, lista i szczegóły.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co możesz zrobić z kontrolką ListView  
  
> [!NOTE]
> Dodatkowy tryb widoku, kafelek jest dostępny tylko w systemie operacyjnym Windows XP i Windows Server 2003. Aby uzyskać więcej informacji, zobacz [jak: Włącz widok kafelków w Windows Forms formancie](how-to-enable-tile-view-in-a-windows-forms-listview-control.md)ListView.  
  
 W trybie widoku LargeIcon są wyświetlane duże ikony obok tekstu elementu. elementy pojawiają się w wielu kolumnach, jeśli formant jest wystarczająco duży. Tryb SmallIcon jest taki sam, z tą różnicą, że wyświetla małe ikony. Tryb listy wyświetla małe ikony, ale zawsze znajduje się w jednej kolumnie. W trybie szczegóły są wyświetlane elementy w wielu kolumnach. Aby uzyskać szczegółowe informacje [, zobacz How to: Dodaj kolumny do kontrolki](how-to-add-columns-to-the-windows-forms-listview-control.md)ListView Windows Forms. Tryb widoku jest określany przez <xref:System.Windows.Forms.ListView.View%2A> właściwość. Wszystkie tryby widoku mogą wyświetlać obrazy z list obrazów. Aby uzyskać szczegółowe informacje [, zobacz How to: Wyświetl ikony dla kontrolki](how-to-display-icons-for-the-windows-forms-listview-control.md)ListView Windows Forms.  
  
 W poniższej tabeli wymieniono niektóre <xref:System.Windows.Forms.ListView> elementy członkowskie i widoki, w których są one ważne.  
  
|Element członkowski ListView|Widok|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A>wartość|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A>wartość|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>Method|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A>wartość|<xref:System.Windows.Forms.View.Details> lub <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem>wydarzen|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A>Method|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>lub<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A>Method|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A>Method|<xref:System.Windows.Forms.View.Details> lub <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A>wartość|Wszystkie widoki z wyjątkiem<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A>wartość|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A>wartość|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>lub<xref:System.Windows.Forms.View.Tile>|  
  
 Właściwość <xref:System.Windows.Forms.ListView> klucza<xref:System.Windows.Forms.ListView.Items%2A>kontrolki, która zawiera elementy wyświetlane przez formant. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Właściwość zawiera kolekcję elementów aktualnie zaznaczonych w kontrolce. Użytkownik może wybrać wiele elementów, na przykład przeciągać i upuszczać kilka elementów jednocześnie do innej kontrolki, jeśli <xref:System.Windows.Forms.ListView.MultiSelect%2A> właściwość jest ustawiona na. `true` Kontrolka może wyświetlać pola wyboru obok elementów, <xref:System.Windows.Forms.ListView.CheckBoxes%2A> Jeśli właściwość jest ustawiona na `true`. <xref:System.Windows.Forms.ListView>  
  
 Właściwość określa typ akcji, które użytkownik musi wykonać, aby aktywować element na liście: opcje są <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>i <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ListView.Activation%2A> <xref:System.Windows.Forms.ItemActivation.OneClick>Aktywacja wymaga jednego kliknięcia, aby aktywować element. <xref:System.Windows.Forms.ItemActivation.TwoClick>Aktywacja wymaga od użytkownika dwukrotnego kliknięcia w celu aktywowania elementu. Pojedyncze kliknięcie zmienia kolor tekstu elementu. <xref:System.Windows.Forms.ItemActivation.Standard>Aktywacja wymaga od użytkownika dwukrotnego kliknięcia, aby aktywować element, ale nie zmienia wyglądu elementu.  
  
 <xref:System.Windows.Forms.ListView> Kontrolka obsługuje również style wizualizacji i inne funkcje dostępne na platformie Windows XP, w tym grupowanie, widok kafelków i znaczniki wstawiania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie kolumn do kontrolki ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetl ikony dla kontrolki ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie elementów SubItems w kolumnach za pomocą kontrolki ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: Wybierz element w kontrolce Windows Forms ListView](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Instrukcje: Grupuj elementy w Windows Forms formancie ListView](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie znacznika wstawiania w Windows Forms formancie ListView](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie funkcji wyszukiwania do formantu ListView](how-to-add-search-capabilities-to-a-listview-control.md)
- [Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Instrukcje: Tworzenie wielookienkowego interfejsu użytkownika z Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
