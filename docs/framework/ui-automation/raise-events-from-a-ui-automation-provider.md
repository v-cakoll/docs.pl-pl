---
title: Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 278fe16bde750e674e456b5f47d9aad29147bdd4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042827"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="d1ae5-102">Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d1ae5-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="d1ae5-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d1ae5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d1ae5-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d1ae5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d1ae5-105">Ten temat zawiera przykładowy kod, który pokazuje, jak zgłosić zdarzenie od dostawcy automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d1ae5-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1ae5-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1ae5-106">Example</span></span>  
 <span data-ttu-id="d1ae5-107">W poniższym przykładzie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie jest zgłaszane w implementacji niestandardowego przycisku kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d1ae5-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="d1ae5-108">Implementacja umożliwia aplikacji klienta automatyzacji interfejsu użytkownika symulowanie kliknięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="d1ae5-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="d1ae5-109">Aby uniknąć niepotrzebnego przetwarzania, przykład <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> sprawdza, czy zdarzenia powinny być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="d1ae5-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="d1ae5-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1ae5-110">See also</span></span>

- [<span data-ttu-id="d1ae5-111">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d1ae5-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
