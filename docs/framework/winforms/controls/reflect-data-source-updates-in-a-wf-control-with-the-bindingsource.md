---
title: Odzwierciedlanie aktualizacji źródła danych w formancie z parametrem BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: f98296b477dbb674cdbdbd8d03e291dd6ca0c8a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742440"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a>Porady: odzwierciedlanie aktualizacji źródła danych w formancie formularzy systemu Windows za pomocą elementu BindingSource
W przypadku korzystania z formantów powiązanych z danymi czasami trzeba odpowiedzieć na zmiany w źródle danych, gdy źródło danych nie zgłosi zdarzeń ze zmienionymi listami. Gdy używasz składnika <xref:System.Windows.Forms.BindingSource>, aby powiązać źródło danych z kontrolką Windows Forms, możesz powiadomić formant o zmianie źródła danych przez wywołanie metody <xref:System.Windows.Forms.BindingSource.ResetBindings%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie metody <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> w celu powiadomienia powiązanej kontrolki dotyczącej aktualizacji w źródle danych.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: powiązanie kontrolki Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
