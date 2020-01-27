---
title: Dostosuj Dodawanie elementów za pomocą składnika BindingSource
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
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738320"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Porady: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows
Gdy używasz składnika <xref:System.Windows.Forms.BindingSource>, aby powiązać formant Windows Forms ze źródłem danych, może się okazać, że konieczne jest dostosowanie tworzenia nowych elementów. Składnik <xref:System.Windows.Forms.BindingSource> ułatwia to poprzez dostarczenie zdarzenia <xref:System.Windows.Forms.BindingSource.AddingNew>, które jest zwykle wywoływane, gdy kontrolka związana wymaga utworzenia nowego elementu. Program obsługi zdarzeń może zapewnić, że wymagane jest zachowanie niestandardowe (na przykład wywołanie metody w usłudze sieci Web lub pobranie nowego obiektu z fabryki klas).  
  
> [!NOTE]
> Gdy element zostanie dodany przez obsługę zdarzenia <xref:System.Windows.Forms.BindingSource.AddingNew>, Dodawanie nie może być anulowane.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak powiązać formant <xref:System.Windows.Forms.DataGridView> z fabryką klas przy użyciu składnika <xref:System.Windows.Forms.BindingSource>. Gdy użytkownik kliknie nowy wiersz kontrolki <xref:System.Windows.Forms.DataGridView>, zdarzenie <xref:System.Windows.Forms.BindingSource.AddingNew> zostanie zgłoszone. Program obsługi zdarzeń tworzy nowy obiekt `DemoCustomer`, który jest przypisany do właściwości <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType>. Powoduje to dodanie nowego obiektu `DemoCustomer` do listy składników <xref:System.Windows.Forms.BindingSource> i zostanie wyświetlony w nowym wierszu kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
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
- [Instrukcje: powiązanie kontrolki Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
