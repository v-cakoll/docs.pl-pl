---
title: Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: 5c14a660481ed14c0d9f379c80f2d6934a3b6dcb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443174"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="58eb3-102">Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker</span><span class="sxs-lookup"><span data-stu-id="58eb3-102">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="58eb3-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="58eb3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="58eb3-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="58eb3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="58eb3-105">Ten temat zawiera przykładowy kod, który pokazuje, jak nawigować między elementami [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przy użyciu klasy <xref:System.Windows.Automation.TreeWalker>.</span><span class="sxs-lookup"><span data-stu-id="58eb3-105">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58eb3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="58eb3-106">Example</span></span>  
 <span data-ttu-id="58eb3-107">Poniższy przykład używa <xref:System.Windows.Automation.TreeWalker.GetParent%2A> do przeszukiwania drzewa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do momentu znalezienia elementu głównego lub pulpitu.</span><span class="sxs-lookup"><span data-stu-id="58eb3-107">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="58eb3-108">Element poniżej, który jest oknem nadrzędnym określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="58eb3-108">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="58eb3-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="58eb3-109">Example</span></span>  
 <span data-ttu-id="58eb3-110">Poniższy przykład używa <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> i <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> do tworzenia <xref:System.Windows.Forms.TreeView>, który pokazuje Całe poddrzewo elementów [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], które znajdują się w widoku kontrolki i są włączone.</span><span class="sxs-lookup"><span data-stu-id="58eb3-110">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="58eb3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58eb3-111">See also</span></span>

- [<span data-ttu-id="58eb3-112">Uzyskiwanie elementów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="58eb3-112">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
