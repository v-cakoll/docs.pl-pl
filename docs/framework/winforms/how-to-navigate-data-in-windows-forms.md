---
title: 'Porady: nawigowanie w danych w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: 9572c1234c07c77d5df0c9cd58499faafe460e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540371"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Porady: nawigowanie w danych w formularzach systemu Windows
W aplikacji Windows, najłatwiejszym sposobem nawigowania rekordy w źródle danych jest powiązać <xref:System.Windows.Forms.BindingSource> składnika do źródła danych, a następnie powiązanie formantów <xref:System.Windows.Forms.BindingSource>. Można następnie użyć metody wbudowanych nawigacji na <xref:System.Windows.Forms.BindingSource> takich <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> i <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Za pomocą następujących metod dostosuje <xref:System.Windows.Forms.BindingSource.Position%2A> i <xref:System.Windows.Forms.BindingSource.Current%2A> właściwości <xref:System.Windows.Forms.BindingSource> odpowiednio. Możesz również znaleźć elementu i ustawić go jako bieżący element przez ustawienie <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Aby zwiększyć pozycji w źródle danych  
  
1.  Ustaw <xref:System.Windows.Forms.BindingSource.Position%2A> właściwość <xref:System.Windows.Forms.BindingSource> powiązane dane pozycja rekordu, aby przejść do. Poniższy przykład przedstawia przy użyciu <xref:System.Windows.Forms.BindingSource.MoveNext%2A> metody <xref:System.Windows.Forms.BindingSource> przyrost <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości podczas `nextButton` zostanie kliknięty. <xref:System.Windows.Forms.BindingSource> Jest skojarzony z `Customers` tabeli zestawu danych `Northwind`.  
  
    > [!NOTE]
    >  Ustawienie <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości na wartość poza pierwszym lub ostatnim rekordzie nie powoduje błąd jako [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie zezwoli na ustaw pozycję na wartość poza granice listy. Jeśli jest to ważne w aplikacji, aby dowiedzieć się czy przeszły poza pierwszym lub ostatnim rekordzie obejmują logiki, aby sprawdzić, czy zostanie przekroczona liczba elementów danych.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Aby sprawdzić, czy przekazanego koniec lub początek  
  
1.  Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzeń. W obsłudze można sprawdzić, czy wartość pozycji proponowanych przekroczyła licznik elementów danych rzeczywistych.  
  
     Poniższy przykład przedstawia, jak można sprawdzić, czy osiągnięto ostatni element danych. W tym przykładzie jest ostatnim elementem **dalej** przycisk w formularzu jest wyłączony.  
  
    > [!NOTE]
    >  Należy pamiętać, że można zmienić listy Nawigacja w kodzie należy ponownie włączyć **dalej** przycisku, dzięki czemu użytkownicy mogą przeglądać przez cały czas nową listę. Ponadto należy pamiętać, że powyższe <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzeń dla konkretnych <xref:System.Windows.Forms.BindingSource> pracujesz musi być skojarzony z metody obsługi zdarzeń. Poniżej przedstawiono przykład metody obsługi <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzeń:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Aby znaleźć element i ustaw go jako bieżący element  
  
1.  Znajdź rekord, który chcesz ustawić jako bieżącego elementu. Można to zrobić za pomocą <xref:System.Windows.Forms.BindingSource.Find%2A> metody <xref:System.Windows.Forms.BindingSource>, jeśli źródło danych implementuje <xref:System.ComponentModel.IBindingList>. Przykładowe dane źródeł, które implementują <xref:System.ComponentModel.IBindingList> są <xref:System.ComponentModel.BindingList%601> i <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Źródła danych obsługiwane przez formularze Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Wiązanie danych i formularzy Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
