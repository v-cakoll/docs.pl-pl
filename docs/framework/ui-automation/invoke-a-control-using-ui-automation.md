---
title: Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: e1b489e8daaaf9f5b8c0cb46374fa54bf165d49c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447004"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="a418a-102">Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a418a-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="a418a-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a418a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a418a-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a418a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a418a-105">W tym temacie przedstawiono sposób wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="a418a-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="a418a-106">Znajdź formant pasujący do określonych warunków właściwości, przenosząc widok kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dla aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="a418a-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="a418a-107">Utwórz <xref:System.Windows.Automation.AutomationElement> dla każdej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a418a-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="a418a-108">Uzyskaj obiekt <xref:System.Windows.Automation.InvokePattern> z dowolnego elementu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] znaleziony, który obsługuje wzorzec kontrolki <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="a418a-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="a418a-109">Użyj <xref:System.Windows.Automation.InvokePattern.Invoke%2A>, aby wywołać formant z programu obsługi zdarzeń klienta.</span><span class="sxs-lookup"><span data-stu-id="a418a-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a418a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a418a-110">Example</span></span>  
 <span data-ttu-id="a418a-111">W tym przykładzie użyto metody <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> klasy <xref:System.Windows.Automation.AutomationElement> do wygenerowania obiektu <xref:System.Windows.Automation.InvokePattern> i wywołania kontrolki przy użyciu metody <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="a418a-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="a418a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a418a-112">See also</span></span>

- [<span data-ttu-id="a418a-113">Przykład InvokePattern, ExpandCollapsePattern i TogglePattern</span><span class="sxs-lookup"><span data-stu-id="a418a-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
