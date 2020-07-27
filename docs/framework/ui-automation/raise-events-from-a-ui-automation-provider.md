---
title: Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika
description: Zobacz przykład pokazujący, jak zgłosić zdarzenie od dostawcy automatyzacji interfejsu użytkownika. Wywołuje zdarzenie automatyzacji interfejsu użytkownika w implementacji niestandardowej kontrolki przycisku.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 75af4d05172e2417d44f76beab486de5eb3a4ba7
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168115"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="38865-104">Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="38865-104">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="38865-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="38865-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="38865-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="38865-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="38865-107">Ten temat zawiera przykładowy kod, który pokazuje, jak zgłosić zdarzenie od dostawcy automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="38865-107">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38865-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="38865-108">Example</span></span>  
 <span data-ttu-id="38865-109">W poniższym przykładzie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie jest zgłaszane w implementacji niestandardowego przycisku kontrolki.</span><span class="sxs-lookup"><span data-stu-id="38865-109">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="38865-110">Implementacja umożliwia aplikacji klienta automatyzacji interfejsu użytkownika symulowanie kliknięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="38865-110">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="38865-111">Aby uniknąć niepotrzebnego przetwarzania, przykład sprawdza, <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> czy zdarzenia powinny być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="38865-111">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="38865-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38865-112">See also</span></span>

- [<span data-ttu-id="38865-113">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="38865-113">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
