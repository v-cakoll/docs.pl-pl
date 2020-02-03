---
title: ListView, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: 9308ff6646704d16b32669827a1f26bebf6958d8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745153"
---
# <a name="listview-control-overview-windows-forms"></a>ListView — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms wyświetla listę elementów z ikonami. Widok listy służy do tworzenia interfejsu użytkownika, takiego jak prawy panel Eksploratora Windows. Kontrolka ma cztery tryby wyświetlania: widoku LargeIcon, SmallIcon, list i details.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co możesz zrobić z kontrolką ListView  
  
> [!NOTE]
> Dodatkowy tryb widoku, kafelek jest dostępny tylko w systemie operacyjnym Windows XP i Windows Server 2003. Aby uzyskać więcej informacji, zobacz [jak: włączyć widok kafelka w kontrolce Windows Forms ListView](how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 W trybie widoku LargeIcon są wyświetlane duże ikony obok tekstu elementu. elementy pojawiają się w wielu kolumnach, jeśli formant jest wystarczająco duży. Tryb SmallIcon jest taki sam, z tą różnicą, że wyświetla małe ikony. Tryb listy wyświetla małe ikony, ale zawsze znajduje się w jednej kolumnie. W trybie szczegóły są wyświetlane elementy w wielu kolumnach. Aby uzyskać szczegółowe informacje, zobacz [jak to zrobić: Dodawanie kolumn do kontrolki ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md). Tryb widoku jest określany przez właściwość <xref:System.Windows.Forms.ListView.View%2A>. Wszystkie tryby widoku mogą wyświetlać obrazy z list obrazów. Aby uzyskać szczegółowe informacje, zobacz [How to: Display Ikons for the Windows Forms ListView Control](how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 W poniższej tabeli wymieniono niektóre elementy członkowskie <xref:System.Windows.Forms.ListView> i widoki, w których są one ważne.  
  
|Element członkowski ListView|Widok|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> Właściwość|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> Właściwość|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>, Metoda|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> Właściwość|<xref:System.Windows.Forms.View.Details> lub <xref:System.Windows.Forms.View.Tile>|  
|zdarzenie <xref:System.Windows.Forms.ListView.DrawSubItem>|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A>, Metoda|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>lub <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A>, Metoda|<xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A>, Metoda|<xref:System.Windows.Forms.View.Details> lub <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> Właściwość|Wszystkie widoki z wyjątkiem <xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> Właściwość|<xref:System.Windows.Forms.View.Details>.,|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> Właściwość|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>lub <xref:System.Windows.Forms.View.Tile>|  
  
 Właściwość klucza kontrolki <xref:System.Windows.Forms.ListView> jest <xref:System.Windows.Forms.ListView.Items%2A>, która zawiera elementy wyświetlane przez formant. Właściwość <xref:System.Windows.Forms.ListView.SelectedItems%2A> zawiera kolekcję elementów aktualnie zaznaczonych w kontrolce. Użytkownik może wybrać wiele elementów, na przykład przeciągać i upuszczać kilka elementów jednocześnie do innej kontrolki, jeśli właściwość <xref:System.Windows.Forms.ListView.MultiSelect%2A> jest ustawiona na `true`. Kontrolka <xref:System.Windows.Forms.ListView> może wyświetlać pola wyboru obok elementów, jeśli właściwość <xref:System.Windows.Forms.ListView.CheckBoxes%2A> jest ustawiona na `true`.  
  
 Właściwość <xref:System.Windows.Forms.ListView.Activation%2A> określa typ akcji, które użytkownik musi wykonać, aby aktywować element na liście: opcje są <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>i <xref:System.Windows.Forms.ItemActivation.TwoClick>. Aktywacja <xref:System.Windows.Forms.ItemActivation.OneClick> wymaga jednego kliknięcia, aby aktywować element. Aktywacja <xref:System.Windows.Forms.ItemActivation.TwoClick> wymaga, aby użytkownik mógł go kliknąć dwukrotnie, aby aktywować element; Pojedyncze kliknięcie zmienia kolor tekstu elementu. Aktywacja <xref:System.Windows.Forms.ItemActivation.Standard> wymaga, aby użytkownik mógł ją uaktywnić, ale nie zmienia wyglądu elementu.  
  
 Kontrolka <xref:System.Windows.Forms.ListView> obsługuje również style wizualizacji i inne funkcje dostępne na platformie Windows XP, w tym grupowanie, widok kafelków i znaczniki wstawiania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: zaznaczanie elementu w kontrolce ListView formularzy Windows Forms](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Instrukcje: grupowanie elementów w kontrolce ListView formularzy Windows Forms](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie znacznika wstawiania w kontrolce ListView formularzy Windows Forms](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Instrukcje: dodawanie funkcji wyszukiwania do kontrolki ListView](how-to-add-search-capabilities-to-a-listview-control.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
