---
title: Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika
description: Użyj automatyzacji interfejsu użytkownika, aby znaleźć formant pasujący do określonych warunków właściwości, utworzyć element AutomationElement, uzyskać InvokePattern i użyć metody Invoke na kontrolce.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 2347a620aab848bf6bcc649a9780aa5a3a520822
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168173"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="efc5d-103">Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="efc5d-103">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="efc5d-104">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="efc5d-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="efc5d-105">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="efc5d-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="efc5d-106">W tym temacie przedstawiono sposób wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="efc5d-106">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="efc5d-107">Znajdź formant pasujący do określonych warunków właściwości, łącząc widok kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa dla aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="efc5d-107">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="efc5d-108">Utwórz <xref:System.Windows.Automation.AutomationElement> dla każdej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="efc5d-108">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="efc5d-109">Uzyskaj <xref:System.Windows.Automation.InvokePattern> obiekt z dowolnego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu, który obsługuje <xref:System.Windows.Automation.InvokePattern> wzorzec kontrolki.</span><span class="sxs-lookup"><span data-stu-id="efc5d-109">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="efc5d-110">Służy <xref:System.Windows.Automation.InvokePattern.Invoke%2A> do wywoływania formantu z programu obsługi zdarzeń klienta.</span><span class="sxs-lookup"><span data-stu-id="efc5d-110">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efc5d-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="efc5d-111">Example</span></span>  
 <span data-ttu-id="efc5d-112">W tym przykładzie użyto <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody <xref:System.Windows.Automation.AutomationElement> klasy do wygenerowania <xref:System.Windows.Automation.InvokePattern> obiektu i wywołania kontrolki przy użyciu <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="efc5d-112">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="efc5d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efc5d-113">See also</span></span>

- [<span data-ttu-id="efc5d-114">Przykład InvokePattern, ExpandCollapsePattern i TogglePattern</span><span class="sxs-lookup"><span data-stu-id="efc5d-114">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
