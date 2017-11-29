---
title: "Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5b3d08c0a6293b6621d9b6debfa4d63c8abaf3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="dc858-102">Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="dc858-102">Traverse Text Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="dc858-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dc858-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="dc858-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="dc858-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="dc858-105">W tym temacie przedstawiono sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przechodzenia zawartość tekstową dokument <xref:System.Windows.Automation.Text.TextUnit> przyrostem.</span><span class="sxs-lookup"><span data-stu-id="dc858-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc858-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc858-106">Example</span></span>  
 <span data-ttu-id="dc858-107">Poniższy przykład kodu pokazuje sposób przenoszenia zawartości dostawcy tekstu automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dc858-107">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="dc858-108"><xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Przenosi metody <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> i <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktów końcowych <xref:System.Windows.Automation.Text.TextPatternRange>.</span><span class="sxs-lookup"><span data-stu-id="dc858-108">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="dc858-109">Ten zakres tekstu jest zwykle degeneracji zakres reprezentujący punkt wstawiania.</span><span class="sxs-lookup"><span data-stu-id="dc858-109">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc858-110">Ponieważ tylko tekstowy osadzonych obiektów są traktowane jako część strumienia tekstu, obiekty osadzone, takie jak obrazy nie wpływają na `Move` lub jego wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="dc858-110">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="dc858-111">Przy użyciu dowolnej metody <xref:System.Windows.Automation.Text.TextUnit> będzie odroczenie do następnego największy <xref:System.Windows.Automation.Text.TextUnit> obsługiwanych w przypadku danego <xref:System.Windows.Automation.Text.TextUnit> nie jest obsługiwana przez formant.</span><span class="sxs-lookup"><span data-stu-id="dc858-111">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc858-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc858-112">See Also</span></span>  
 [<span data-ttu-id="dc858-113">Przegląd automatyzacji interfejsu użytkownika — TextPattern</span><span class="sxs-lookup"><span data-stu-id="dc858-113">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="dc858-114">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="dc858-114">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="dc858-115">Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="dc858-115">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="dc858-116">Przegląd wzorców formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="dc858-116">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="dc858-117">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="dc858-117">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
