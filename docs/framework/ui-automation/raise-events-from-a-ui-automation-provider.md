---
title: Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 1a940cbb99ac068dad6c366520a544035270da3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446879"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="48590-102">Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="48590-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="48590-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="48590-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="48590-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="48590-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="48590-105">Ten temat zawiera przykładowy kod, który pokazuje, jak zgłosić zdarzenie od dostawcy automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="48590-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48590-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="48590-106">Example</span></span>  
 <span data-ttu-id="48590-107">W poniższym przykładzie zdarzenie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest zgłaszane w implementacji niestandardowego przycisku kontrolki.</span><span class="sxs-lookup"><span data-stu-id="48590-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="48590-108">Implementacja umożliwia aplikacji klienta automatyzacji interfejsu użytkownika symulowanie kliknięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="48590-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="48590-109">Aby uniknąć niepotrzebnego przetwarzania, przykład sprawdza <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>, aby sprawdzić, czy zdarzenia powinny być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="48590-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="48590-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48590-110">See also</span></span>

- [<span data-ttu-id="48590-111">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="48590-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
