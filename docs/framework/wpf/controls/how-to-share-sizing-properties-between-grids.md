---
title: "Jak udostępniać właściwości ustalania rozmiaru miedzy siatkami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8f80d93f9625ff962a3e3fab1f6647678ecf32f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="0c6c9-102">Jak udostępniać właściwości ustalania rozmiaru miedzy siatkami</span><span class="sxs-lookup"><span data-stu-id="0c6c9-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="0c6c9-103">W tym przykładzie pokazano, jak udostępniać dane zmiany rozmiaru kolumn i wierszy między <xref:System.Windows.Controls.Grid> elementy, aby zachować zmiany rozmiaru spójne.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c6c9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c6c9-104">Example</span></span>  
 <span data-ttu-id="0c6c9-105">Poniższy przykład przedstawia dwa <xref:System.Windows.Controls.Grid> jako elementy podrzędne elementu nadrzędnego <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="0c6c9-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Dołączona właściwość <xref:System.Windows.Controls.Grid> jest zdefiniowany w nadrzędnej <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="0c6c9-107">Przykład manipuluje wartość właściwości przy użyciu dwóch <xref:System.Windows.Controls.Button> elementy; każdy element reprezentuje jednej wartości właściwości typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="0c6c9-108">Gdy <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> ma ustawioną wartość właściwości `true`, każdy członek kolumny lub wiersza z <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> udostępnia informacje dotyczące zmiany rozmiaru, niezależnie od zawartości wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="0c6c9-109">...</span><span class="sxs-lookup"><span data-stu-id="0c6c9-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="0c6c9-110">W poniższym przykładzie kodu powiązanego obsługuje metody który przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zgłasza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="0c6c9-111">W przykładzie polecenie zapisuje wyniki tych wywołań metody <xref:System.Windows.Controls.TextBlock> elementów powiązanych Użyj get metody zwracać wartości właściwości jako ciągi.</span><span class="sxs-lookup"><span data-stu-id="0c6c9-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0c6c9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c6c9-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [<span data-ttu-id="0c6c9-113">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="0c6c9-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
