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
ms.openlocfilehash: f17f3ad25f137bbf8d7cf88b43cc52dfdeeb3fd4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923723"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="570ff-102">Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="570ff-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="570ff-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="570ff-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="570ff-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="570ff-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="570ff-105">W tym temacie przedstawiono sposób wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="570ff-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="570ff-106">Znajdź formant pasujący do określonych warunków właściwości, łącząc widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolki drzewa dla aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="570ff-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="570ff-107"><xref:System.Windows.Automation.AutomationElement> Utwórz dla każdej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="570ff-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="570ff-108">Uzyskaj obiekt z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dowolnego<xref:System.Windows.Automation.InvokePattern> elementu, który obsługuje wzorzec kontrolki. <xref:System.Windows.Automation.InvokePattern></span><span class="sxs-lookup"><span data-stu-id="570ff-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="570ff-109">Służy <xref:System.Windows.Automation.InvokePattern.Invoke%2A> do wywoływania formantu z programu obsługi zdarzeń klienta.</span><span class="sxs-lookup"><span data-stu-id="570ff-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="570ff-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="570ff-110">Example</span></span>  
 <span data-ttu-id="570ff-111">W tym przykładzie użyto <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody <xref:System.Windows.Automation.AutomationElement> klasy do wygenerowania <xref:System.Windows.Automation.InvokePattern> <xref:System.Windows.Automation.InvokePattern.Invoke%2A> obiektu i wywołania kontrolki przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="570ff-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="570ff-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="570ff-112">See also</span></span>

- [<span data-ttu-id="570ff-113">Przykład InvokePattern, ExpandCollapsePattern i TogglePattern</span><span class="sxs-lookup"><span data-stu-id="570ff-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
