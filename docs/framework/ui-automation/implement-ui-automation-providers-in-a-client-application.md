---
title: Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 102a2fe1cb2598078af7246d5f88df928064693f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676645"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="e2089-102">Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta</span><span class="sxs-lookup"><span data-stu-id="e2089-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
>  <span data-ttu-id="e2089-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e2089-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e2089-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e2089-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e2089-105">Ten temat zawiera przykładowy kod, który pokazuje, jak do implementowania dostawcy automatyzacji interfejsu użytkownika po stronie klienta w obrębie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2089-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="e2089-106">Jest to rzadkie scenariusz.</span><span class="sxs-lookup"><span data-stu-id="e2089-106">This is an uncommon scenario.</span></span> <span data-ttu-id="e2089-107">W większości przypadków automatyzacji interfejsu użytkownika aplikacja kliencka korzysta z dostawcy po stronie serwera lub dostawcy po stronie klienta, które znajdują się w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="e2089-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2089-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2089-108">Example</span></span>  
 <span data-ttu-id="e2089-109">Poniższy przykład kodu implementuje prostego dostawcy okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="e2089-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="e2089-110">Kod nie ma wszystkie przydatne funkcje, ale jest przeznaczona do zademonstrowania podstawowe kroki tworzenia dostawcy w obrębie kodu klienta i rejestrując ją za pomocą <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2089-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="e2089-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2089-111">See also</span></span>
- [<span data-ttu-id="e2089-112">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e2089-112">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="e2089-113">Rejestrowanie zestawów dostawcy po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="e2089-113">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="e2089-114">Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="e2089-114">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="e2089-115">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="e2089-115">Client-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
