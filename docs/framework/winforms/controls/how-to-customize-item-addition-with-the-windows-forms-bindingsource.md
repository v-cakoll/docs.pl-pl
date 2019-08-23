---
title: 'Instrukcje: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 59522791408eb9c8cabf97a62be2049aeb17f864
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935349"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Instrukcje: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows
Gdy używasz <xref:System.Windows.Forms.BindingSource> składnika, aby powiązać formant Windows Forms ze źródłem danych, może się okazać, że konieczne jest dostosowanie tworzenia nowych elementów. Składnik ten zapewnia prostą, <xref:System.Windows.Forms.BindingSource.AddingNew> dostarczając zdarzenie, które jest zwykle wywoływane, gdy kontrolka powiązania musi utworzyć nowy element. <xref:System.Windows.Forms.BindingSource> Program obsługi zdarzeń może zapewnić, że wymagane jest zachowanie niestandardowe (na przykład wywołanie metody w usłudze sieci Web lub pobranie nowego obiektu z fabryki klas).  
  
> [!NOTE]
> Gdy element zostanie dodany przez obsługę <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenia, Dodawanie nie może być anulowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób powiązania <xref:System.Windows.Forms.DataGridView> kontrolki z fabryką klas przy <xref:System.Windows.Forms.BindingSource> użyciu składnika. Gdy użytkownik kliknie <xref:System.Windows.Forms.DataGridView> nowy wiersz kontrolki <xref:System.Windows.Forms.BindingSource.AddingNew> , zdarzenie jest zgłaszane. Program obsługi zdarzeń tworzy nowy `DemoCustomer` obiekt, który jest przypisany <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> do właściwości. Powoduje to, że `DemoCustomer` nowy obiekt zostanie dodany <xref:System.Windows.Forms.BindingSource> do listy składników i zostanie wyświetlony w nowym wierszu <xref:System.Windows.Forms.DataGridView> formantu.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: Powiąż formant Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
