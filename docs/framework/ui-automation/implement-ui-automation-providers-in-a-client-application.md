---
title: Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta
description: Zobacz przykład sposobu implementacji dostawcy automatyzacji interfejsu użytkownika po stronie klienta w aplikacji. Należy zauważyć, że jest to typowy scenariusz.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: c604b68021886abdf06360bfb8afefe3640c12fe
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164123"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="5c8e1-104">Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta</span><span class="sxs-lookup"><span data-stu-id="5c8e1-104">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
> <span data-ttu-id="5c8e1-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5c8e1-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5c8e1-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="5c8e1-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5c8e1-107">Ten temat zawiera przykładowy kod pokazujący sposób implementacji dostawcy automatyzacji interfejsu użytkownika po stronie klienta w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c8e1-107">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="5c8e1-108">Jest to typowy scenariusz.</span><span class="sxs-lookup"><span data-stu-id="5c8e1-108">This is an uncommon scenario.</span></span> <span data-ttu-id="5c8e1-109">Najczęściej aplikacja klienta automatyzacji interfejsu użytkownika korzysta z dostawców po stronie serwera lub dostawców po stronie klienta, które znajdują się w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="5c8e1-109">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c8e1-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c8e1-110">Example</span></span>  
 <span data-ttu-id="5c8e1-111">Poniższy przykładowy kod implementuje prostego dostawcę dla okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="5c8e1-111">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="5c8e1-112">Kod nie ma żadnych użytecznych funkcji, ale jest przeznaczony do zademonstrowania podstawowych kroków konfigurowania dostawcy w kodzie klienta i rejestrowania go za pomocą programu <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A> .</span><span class="sxs-lookup"><span data-stu-id="5c8e1-112">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="5c8e1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c8e1-113">See also</span></span>

- [<span data-ttu-id="5c8e1-114">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="5c8e1-114">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="5c8e1-115">Rejestrowanie zestawów dostawcy po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="5c8e1-115">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="5c8e1-116">Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="5c8e1-116">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="5c8e1-117">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="5c8e1-117">Client-Side UI Automation Provider Implementation</span></span>](client-side-ui-automation-provider-implementation.md)
