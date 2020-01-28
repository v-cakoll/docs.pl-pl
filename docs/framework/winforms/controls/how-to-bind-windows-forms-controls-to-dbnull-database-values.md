---
title: Powiązywanie kontrolek z wartościami bazy danych DBNull
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746661"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Porady: powiązanie formantów formularzy systemu Windows z wartościami bazy danych DBNull
Po powiązaniu Windows Forms formantów ze źródłem danych, gdy źródło danych zwróci wartość <xref:System.DBNull>, można zastąpić odpowiednią wartość bez obsługi, formatowania lub analizowania zdarzeń. Właściwość <xref:System.Windows.Forms.Binding.NullValue%2A> będzie konwertowana <xref:System.DBNull> do określonego obiektu podczas formatowania lub analizowania wartości źródła danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób powiązania wartości <xref:System.DBNull> w dwóch różnych sytuacjach. Pierwszy pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> dla właściwości ciągu; Drugi pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> dla właściwości obrazu.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Typy powiązanej właściwości i właściwości <xref:System.Windows.Forms.Binding.NullValue%2A> muszą być takie same lub mogą wystąpić błędy, a żadne dalsze wartości <xref:System.Windows.Forms.Binding.NullValue%2A> nie zostaną przetworzone. W tej sytuacji wyjątek nie zostanie wygenerowany.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: obsługa błędów i wyjątków występujących za powodu powiązania danych](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Instrukcje: powiązanie kontrolki Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
