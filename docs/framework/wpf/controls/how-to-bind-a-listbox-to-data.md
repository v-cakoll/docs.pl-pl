---
title: 'Instrukcje: Powiązywanie ListBox z danymi'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 4dea53a524247d18628b3e7e7b2c06906dced53d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106444"
---
# <a name="how-to-bind-a-listbox-to-data"></a>Instrukcje: Powiązywanie ListBox z danymi
Twórca aplikacji może utworzyć <xref:System.Windows.Controls.ListBox> formantów bez określania zawartość każdej <xref:System.Windows.Controls.ListBoxItem> oddzielnie. Powiązanie danych można użyć, aby powiązać dane do poszczególnych elementów.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.ListBox> który wypełnia <xref:System.Windows.Controls.ListBoxItem> elementów przez powiązanie danych do źródła danych o nazwie *kolory*. W takim przypadku nie jest konieczne użycie <xref:System.Windows.Controls.ListBoxItem> tagów, aby określić zawartość każdego elementu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[ListBoxEvent#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [Kontrolki](../advanced/optimizing-performance-controls.md)
