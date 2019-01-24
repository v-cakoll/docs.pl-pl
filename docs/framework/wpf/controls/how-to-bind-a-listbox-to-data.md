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
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="01b85-102">Instrukcje: Powiąż ListBox z danymi</span><span class="sxs-lookup"><span data-stu-id="01b85-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="01b85-103">Twórca aplikacji może utworzyć <xref:System.Windows.Controls.ListBox> formantów bez określania zawartość każdej <xref:System.Windows.Controls.ListBoxItem> oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="01b85-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="01b85-104">Powiązanie danych można użyć, aby powiązać dane do poszczególnych elementów.</span><span class="sxs-lookup"><span data-stu-id="01b85-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="01b85-105">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.ListBox> który wypełnia <xref:System.Windows.Controls.ListBoxItem> elementów przez powiązanie danych do źródła danych o nazwie *kolory*.</span><span class="sxs-lookup"><span data-stu-id="01b85-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="01b85-106">W takim przypadku nie jest konieczne użycie <xref:System.Windows.Controls.ListBoxItem> tagów, aby określić zawartość każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="01b85-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01b85-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="01b85-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="01b85-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01b85-108">See also</span></span>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [<span data-ttu-id="01b85-109">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="01b85-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
