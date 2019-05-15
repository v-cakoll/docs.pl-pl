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
ms.openlocfilehash: 94c7b304dd8b909d60ef6b25f828524594caf886
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592816"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Instrukcje: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows
Kiedy używasz <xref:System.Windows.Forms.BindingSource> składnika, aby powiązać formant programu Windows Forms ze źródłem danych może okazać się konieczne dostosowanie tworzenia nowych elementów. <xref:System.Windows.Forms.BindingSource> Ze składników zgłasza to prosta, zapewniając <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie, które zazwyczaj jest inicjowane, gdy formant związany potrzebne do utworzenia nowego elementu. Procedury obsługi zdarzenia może zapewnić dowolne niestandardowe zachowanie jest wymagana (na przykład, wywołanie metody usługi sieci Web lub wprowadzenie nowego obiektu z fabryki klas).  
  
> [!NOTE]
>  Gdy element zostanie dodany do obsługi <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzeń, nie można anulować dodawanie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Forms.DataGridView> kontrolki fabryki klas przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. Kiedy użytkownik kliknie <xref:System.Windows.Forms.DataGridView> kontrolki nowy wiersz <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie jest wywoływane. Program obsługi zdarzeń tworzy nową `DemoCustomer` obiektu, który jest przypisany do <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> właściwości. Powoduje to, że nowe `DemoCustomer` obiektów, które mają zostać dodane do <xref:System.Windows.Forms.BindingSource> listy składnika i mają być wyświetlane w nowym wierszu <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: Powiązanie z typem formantu Windows Forms](how-to-bind-a-windows-forms-control-to-a-type.md)
