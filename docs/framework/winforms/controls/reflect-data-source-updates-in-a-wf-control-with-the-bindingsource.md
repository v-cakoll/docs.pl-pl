---
title: 'Instrukcje: odzwierciedlanie aktualizacji źródła danych w kontrolce formularzy systemu Windows za pomocą elementu BindingSource'
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
ms.openlocfilehash: 16dbe4da1efecd120d4da4d66c3d79ec907b92a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218655"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a>Instrukcje: odzwierciedlanie aktualizacji źródła danych w kontrolce formularzy systemu Windows za pomocą elementu BindingSource
Korzystając z formantów powiązanych z danymi, czasami konieczne reagowanie na zmiany w źródle danych, gdy źródło danych nie powoduje zmiany listy zdarzeń. Kiedy używasz <xref:System.Windows.Forms.BindingSource> składnika można powiązać źródła danych do kontrolki formularzy Windows może powiadomić kontrolkę źródle danych została zmieniona przez wywołanie metody <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> — metoda.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób użycia <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> metody powiadamianie powiązanego formantu o aktualizacji w źródle danych.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: Powiązanie z typem formantu Windows Forms](how-to-bind-a-windows-forms-control-to-a-type.md)
