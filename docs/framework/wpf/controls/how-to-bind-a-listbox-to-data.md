---
title: 'Instrukcje: Powiąż ListBox z danymi'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 6d37cda057ea1e7ca6761363857a2647da37afee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650655"
---
# <a name="how-to-bind-a-listbox-to-data"></a>Instrukcje: Powiąż ListBox z danymi
Twórca aplikacji może utworzyć <xref:System.Windows.Controls.ListBox> formantów bez określania zawartość każdej <xref:System.Windows.Controls.ListBoxItem> oddzielnie. Powiązanie danych można użyć, aby powiązać dane do poszczególnych elementów.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.ListBox> który wypełnia <xref:System.Windows.Controls.ListBoxItem> elementów przez powiązanie danych do źródła danych o nazwie *kolory*. W takim przypadku nie jest konieczne użycie <xref:System.Windows.Controls.ListBoxItem> tagów, aby określić zawartość każdego elementu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [Kontrolki](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
