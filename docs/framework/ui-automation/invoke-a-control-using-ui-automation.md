---
title: "Wywoływanie formantu przy użyciu automatyzacji interfejsu użytkownika"
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
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 76b52129c0eab30bccde02389142bee2123e64f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="f06a6-102">Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f06a6-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="f06a6-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f06a6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f06a6-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="f06a6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f06a6-105">W tym temacie przedstawiono sposób wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="f06a6-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f06a6-106">Odnaleźć formantu, który spełnia warunki określoną właściwość przez krótki formantu widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa dla aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="f06a6-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
-   <span data-ttu-id="f06a6-107">Utwórz <xref:System.Windows.Automation.AutomationElement> dla każdego formantu.</span><span class="sxs-lookup"><span data-stu-id="f06a6-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
-   <span data-ttu-id="f06a6-108">Uzyskaj <xref:System.Windows.Automation.InvokePattern> obiektu za pomocą dowolnego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] znaleziony element, który obsługuje <xref:System.Windows.Automation.InvokePattern> — wzorzec formantu.</span><span class="sxs-lookup"><span data-stu-id="f06a6-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
-   <span data-ttu-id="f06a6-109">Użyj <xref:System.Windows.Automation.InvokePattern.Invoke%2A> do wywołania formantu z obsługi zdarzeń klienta.</span><span class="sxs-lookup"><span data-stu-id="f06a6-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f06a6-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f06a6-110">Example</span></span>  
 <span data-ttu-id="f06a6-111">W tym przykładzie użyto <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody <xref:System.Windows.Automation.AutomationElement> klasy do wygenerowania <xref:System.Windows.Automation.InvokePattern> obiektu i wywoływanie formantu przy użyciu <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f06a6-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="f06a6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f06a6-112">See Also</span></span>  
 [<span data-ttu-id="f06a6-113">Klasy InvokePattern i przykładowego elementu Menu klasy ExpandCollapsePattern</span><span class="sxs-lookup"><span data-stu-id="f06a6-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
