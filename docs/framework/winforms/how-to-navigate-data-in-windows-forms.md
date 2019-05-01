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
ms.openlocfilehash: 2ba33f9ecb3a12a62c41af17d3f9ad6f6e3f8a5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801715"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Instrukcje: Nawigowanie po danych w formularzach Windows Forms
W aplikacji Windows, aby poruszać się po rekordów w źródle danych najłatwiej można powiązać <xref:System.Windows.Forms.BindingSource> składnik do źródła danych, a następnie kontrolki powiązania <xref:System.Windows.Forms.BindingSource>. Można następnie użyć metody wbudowanej nawigacji na <xref:System.Windows.Forms.BindingSource> takich <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> i <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Przy użyciu tych metod skoryguje <xref:System.Windows.Forms.BindingSource.Position%2A> i <xref:System.Windows.Forms.BindingSource.Current%2A> właściwości <xref:System.Windows.Forms.BindingSource> odpowiednio. Można również znaleźć element i ustaw go jako bieżący element ustawiając <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Aby dodać kolejne stanowisko w źródle danych  
  
1. Ustaw <xref:System.Windows.Forms.BindingSource.Position%2A> właściwość <xref:System.Windows.Forms.BindingSource> pozycja rekordu, aby przejść do powiązanych danych. Poniższy przykład ilustruje użycie <xref:System.Windows.Forms.BindingSource.MoveNext%2A> metody <xref:System.Windows.Forms.BindingSource> do następującej <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości podczas `nextButton` kliknięciu. <xref:System.Windows.Forms.BindingSource> Jest skojarzony z `Customers` tabeli zestawu danych `Northwind`.  
  
    > [!NOTE]
    >  Ustawienie <xref:System.Windows.Forms.BindingSource.Position%2A> właściwość z wartością poza pierwszy lub ostatni rekord nie powoduje wystąpienie błędu, jako [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie zezwoli na ustawienie pozycji do wartości poza granice listy. Jeśli jest to ważne w aplikacji, aby dowiedzieć się, czy wykonano ostatnie pierwszy lub ostatni rekord, obejmują logikę w celu sprawdzenia, czy przekroczy liczba elementów danych.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Aby sprawdzić, czy ukończyli koniec lub początek  
  
1. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzeń. W procedurze obsługi możesz sprawdzić, czy wartość pozycji proponowane przekroczyła liczba elementów danych rzeczywistych.  
  
     W poniższym przykładzie pokazano, jak można sprawdzić, czy osiągnięto ostatniego elementu danych. W tym przykładzie, jeśli jesteś w ostatnim elemencie **dalej** przycisku w formularzu jest wyłączona.  
  
    > [!NOTE]
    >  Należy pamiętać, że powinno zmienić listy Nawigacja w kodzie, należy włączyć ponownie **dalej** przycisk Tak, aby użytkownicy mogą przeglądać cały czas nową listę. Ponadto należy pamiętać, który powyższych <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzenia dla określonego <xref:System.Windows.Forms.BindingSource> pracujesz z musi być skojarzone z jego metody obsługi zdarzeń. Oto przykład metody obsługi <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzeń:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Aby znaleźć element i ustaw go jako bieżący element  
  
1. Znajdź rekord, który chcesz ustawić jako bieżący element. Można to zrobić za pomocą <xref:System.Windows.Forms.BindingSource.Find%2A> metody <xref:System.Windows.Forms.BindingSource>, jeśli dane źródłowe implementuje <xref:System.ComponentModel.IBindingList>. Przykłady danych źródła, które implementują <xref:System.ComponentModel.IBindingList> są <xref:System.ComponentModel.BindingList%601> i <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Źródła danych obsługiwane przez formularze Windows Forms](data-sources-supported-by-windows-forms.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
