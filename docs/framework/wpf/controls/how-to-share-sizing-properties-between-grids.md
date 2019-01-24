---
title: 'Instrukcje: Udostępniaj właściwości ustalania rozmiaru miedzy siatkami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: e415cb8bf5d2eb53926ae885ba18685390a61201
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694103"
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="3248a-102">Instrukcje: Udostępniaj właściwości ustalania rozmiaru miedzy siatkami</span><span class="sxs-lookup"><span data-stu-id="3248a-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="3248a-103">W tym przykładzie pokazano, jak udostępnianie danych zmiany rozmiaru kolumn i wierszy między <xref:System.Windows.Controls.Grid> elementów, aby zachować zmiany rozmiaru spójne.</span><span class="sxs-lookup"><span data-stu-id="3248a-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3248a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3248a-104">Example</span></span>  
 <span data-ttu-id="3248a-105">Poniższy przykład przedstawia dwa <xref:System.Windows.Controls.Grid> jako elementy podrzędne elementu nadrzędnego <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3248a-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="3248a-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Dołączonych właściwości <xref:System.Windows.Controls.Grid> jest zdefiniowany w nadrzędnej <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3248a-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="3248a-107">Przykład manipuluje wartości właściwości, używając dwóch <xref:System.Windows.Controls.Button> elementów; każdy element reprezentuje jedną z wartości właściwości typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="3248a-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="3248a-108">Gdy <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> wartość właściwości jest równa `true`, każdego wiersza lub kolumny elementu członkowskiego <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> udostępnia informacje dotyczące zmiany rozmiaru, niezależnie od tego, zawartość wiersza lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="3248a-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="3248a-109">...</span><span class="sxs-lookup"><span data-stu-id="3248a-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="3248a-110">W poniższym przykładzie związanym z kodem obsługuje metody, przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3248a-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="3248a-111">W przykładzie polecenie zapisuje wyniki tych wywołań metody <xref:System.Windows.Controls.TextBlock> elementy, które są związane z użycia metod get na dane wyjściowe nowe wartości właściwości jako ciągi.</span><span class="sxs-lookup"><span data-stu-id="3248a-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3248a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3248a-112">See also</span></span>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [<span data-ttu-id="3248a-113">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="3248a-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
