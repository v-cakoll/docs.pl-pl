---
title: Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker
description: Zobacz przykład kodu, który pokazuje, jak nawigować między elementami automatyzacji interfejsu użytkownika za pomocą klasy użyciu opcji TreeWalker.
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
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168019"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="cd373-103">Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker</span><span class="sxs-lookup"><span data-stu-id="cd373-103">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="cd373-104">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cd373-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cd373-105">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cd373-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cd373-106">Ten temat zawiera przykładowy kod, który pokazuje, jak przechodzić między [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementami przy użyciu <xref:System.Windows.Automation.TreeWalker> klasy.</span><span class="sxs-lookup"><span data-stu-id="cd373-106">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd373-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd373-107">Example</span></span>  
 <span data-ttu-id="cd373-108">Poniższy przykład używa do przeszukiwania <xref:System.Windows.Automation.TreeWalker.GetParent%2A> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] drzewa do momentu znalezienia elementu głównego lub pulpitu.</span><span class="sxs-lookup"><span data-stu-id="cd373-108">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="cd373-109">Element poniżej, który jest oknem nadrzędnym określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="cd373-109">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="cd373-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd373-110">Example</span></span>  
 <span data-ttu-id="cd373-111">Poniższy przykład używa <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> i <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> do tworzenia <xref:System.Windows.Forms.TreeView> , który pokazuje Całe poddrzewo elementów znajdujących [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] się w widoku kontrolki, które są włączone.</span><span class="sxs-lookup"><span data-stu-id="cd373-111">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="cd373-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd373-112">See also</span></span>

- [<span data-ttu-id="cd373-113">Uzyskiwanie elementów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cd373-113">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
