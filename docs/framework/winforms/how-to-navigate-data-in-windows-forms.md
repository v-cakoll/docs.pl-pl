---
title: 'Instrukcje: Nawigowanie po danych w formularzach Windows Forms'
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
ms.openlocfilehash: eb973497f51592b5d34c22e62da77612aec23c35
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964278"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Instrukcje: Nawigowanie po danych w formularzach Windows Forms
W aplikacji systemu Windows Najprostszym sposobem nawigowania po rekordach w źródle danych jest powiązanie <xref:System.Windows.Forms.BindingSource> składnika ze źródłem danych, a następnie powiązanie kontrolek <xref:System.Windows.Forms.BindingSource>z. Następnie można <xref:System.Windows.Forms.BindingSource> użyć wbudowanej metody nawigacji w <xref:System.Windows.Forms.BindingSource.MoveNext%2A>taki sposób, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> i <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Zastosowanie tych metod spowoduje dostosowanie <xref:System.Windows.Forms.BindingSource.Position%2A> <xref:System.Windows.Forms.BindingSource> odpowiednio właściwości <xref:System.Windows.Forms.BindingSource.Current%2A> i. Możesz również znaleźć element i ustawić go jako bieżący element przez ustawienie <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Aby zwiększyć położenie w źródle danych  
  
1. <xref:System.Windows.Forms.BindingSource.Position%2A> Ustaw właściwość <xref:System.Windows.Forms.BindingSource> dla danych powiązanych z pozycją rekord, aby przejść do. Poniższy przykład <xref:System.Windows.Forms.BindingSource.MoveNext%2A> ilustruje użycie metody, aby `nextButton` zwiększyć <xref:System.Windows.Forms.BindingSource.Position%2A> Właściwość <xref:System.Windows.Forms.BindingSource> , gdy zostanie kliknięty. Jest skojarzona `Customers` z tabelą zestawu danych `Northwind`. <xref:System.Windows.Forms.BindingSource>  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource.Position%2A> Ustawienie właściwości na wartość spoza pierwszego lub ostatniego rekordu nie powoduje błędu, ponieważ .NET Framework nie umożliwi ustawienia pozycji do wartości poza granicami listy... Jeśli w aplikacji jest ważne, aby dowiedzieć się, czy poprzedni pierwszy lub ostatni rekord został usunięty, Dołącz logikę, aby sprawdzić, czy przekroczy liczbę elementów danych.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Aby sprawdzić, czy przeszedł koniec lub początek  
  
1. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzenia. W programie obsługi można sprawdzić, czy proponowana wartość pozycji przekroczyła rzeczywistą liczbę elementów danych.  
  
     Poniższy przykład ilustruje, jak można sprawdzić, czy osiągnięto ostatni element danych. W przykładzie, jeśli używasz ostatniego elementu, przycisk **dalej** na formularzu jest wyłączony.  
  
    > [!NOTE]
    > Należy pamiętać, że w przypadku zmiany listy, która jest przeszukiwana w kodzie, należy ponownie włączyć przycisk **dalej** , aby użytkownicy mogli przeglądać całą długość nowej listy. Ponadto należy pamiętać, że powyższe <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzenie dotyczące konkretnego <xref:System.Windows.Forms.BindingSource> , z którym pracujesz, musi być skojarzone z jego metodą obsługi zdarzeń. Poniżej znajduje się przykład metody obsługi <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzenia:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Aby znaleźć element i ustawić go jako bieżący element  
  
1. Znajdź rekord, który ma zostać ustawiony jako bieżący element. Można to zrobić przy użyciu <xref:System.Windows.Forms.BindingSource.Find%2A> metody <xref:System.Windows.Forms.BindingSource>, jeśli źródło danych implementuje <xref:System.ComponentModel.IBindingList>. Niektóre przykłady źródeł danych, które <xref:System.ComponentModel.IBindingList> implementują <xref:System.ComponentModel.BindingList%601> to <xref:System.Data.DataView>i.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Źródła danych obsługiwane przez formularze Windows Forms](data-sources-supported-by-windows-forms.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
