---
title: Jak powiązać ListBox z danymi
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 186d25750c5ce196a5e46c02f0f56e2440ea3a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="67c65-102">Jak powiązać ListBox z danymi</span><span class="sxs-lookup"><span data-stu-id="67c65-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="67c65-103">Deweloper aplikacji można utworzyć <xref:System.Windows.Controls.ListBox> formantów bez określania zawartości każdego <xref:System.Windows.Controls.ListBoxItem> oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="67c65-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="67c65-104">Powiązanie danych służy do powiązania danych do poszczególnych elementów.</span><span class="sxs-lookup"><span data-stu-id="67c65-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="67c65-105">Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.ListBox> który wypełnia <xref:System.Windows.Controls.ListBoxItem> elementów przez powiązanie danych ze źródłem danych o nazwie *kolory*.</span><span class="sxs-lookup"><span data-stu-id="67c65-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="67c65-106">W takim przypadku nie jest konieczne użycie <xref:System.Windows.Controls.ListBoxItem> tagi umożliwia określenie zawartości każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="67c65-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67c65-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="67c65-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="67c65-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67c65-108">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [<span data-ttu-id="67c65-109">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="67c65-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
