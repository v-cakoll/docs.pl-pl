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
ms.openlocfilehash: ef3d03bee412b97ed88ec76e81ad2fd19a9595eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968946"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="b0411-102">Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta</span><span class="sxs-lookup"><span data-stu-id="b0411-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
> <span data-ttu-id="b0411-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b0411-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b0411-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0411-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b0411-105">Ten temat zawiera przykładowy kod pokazujący sposób implementacji dostawcy automatyzacji interfejsu użytkownika po stronie klienta w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0411-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="b0411-106">Jest to typowy scenariusz.</span><span class="sxs-lookup"><span data-stu-id="b0411-106">This is an uncommon scenario.</span></span> <span data-ttu-id="b0411-107">Najczęściej aplikacja klienta automatyzacji interfejsu użytkownika korzysta z dostawców po stronie serwera lub dostawców po stronie klienta, które znajdują się w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="b0411-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0411-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0411-108">Example</span></span>  
 <span data-ttu-id="b0411-109">Poniższy przykładowy kod implementuje prostego dostawcę dla okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="b0411-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="b0411-110">Kod nie ma żadnych użytecznych funkcji, ale jest przeznaczony do zademonstrowania podstawowych kroków konfigurowania dostawcy w kodzie klienta i rejestrowania go za pomocą programu <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0411-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="b0411-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0411-111">See also</span></span>

- [<span data-ttu-id="b0411-112">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="b0411-112">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="b0411-113">Rejestrowanie zestawów dostawcy po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="b0411-113">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="b0411-114">Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="b0411-114">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="b0411-115">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="b0411-115">Client-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
