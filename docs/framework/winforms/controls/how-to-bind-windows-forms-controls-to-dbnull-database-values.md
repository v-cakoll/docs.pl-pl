---
title: 'Instrukcje: wiązanie kontrolek formularzy systemu Windows z wartościami bazy danych DBNull'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 8abce5d69a7cece6528e0c9d8728de0e0acd9305
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591426"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Instrukcje: wiązanie kontrolek formularzy systemu Windows z wartościami bazy danych DBNull
Po powiązaniu kontrolek formularzy Windows Forms do źródła danych i źródła danych zwraca <xref:System.DBNull> wartość odpowiednią wartość można zastąpić bez obsługi, formatowanie i analizowanie zdarzeń. <xref:System.Windows.Forms.Binding.NullValue%2A> Przekonwertuje właściwość <xref:System.DBNull> podanemu obiektowi podczas formatowania lub analizowania wartości źródła danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak powiązać <xref:System.DBNull> wartości w dwóch różnych sytuacjach. Pierwszy pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> dla właściwości ciągu; drugi pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> właściwości obrazu.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Typy właściwości powiązanej i <xref:System.Windows.Forms.Binding.NullValue%2A> właściwości musi być taka sama lub spowoduje błąd żadnych dalszych <xref:System.Windows.Forms.Binding.NullValue%2A> wartości zostaną przetworzone. W takiej sytuacji nie zostanie zgłoszony wyjątek.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: Obsługa błędów i wyjątków występujących za powodu powiązania danych](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Instrukcje: Powiązanie z typem formantu Windows Forms](how-to-bind-a-windows-forms-control-to-a-type.md)
