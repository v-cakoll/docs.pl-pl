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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 29ff34c715315e60875384e4deba440e00098ba9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="8db37-102">Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta</span><span class="sxs-lookup"><span data-stu-id="8db37-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
>  <span data-ttu-id="8db37-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8db37-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8db37-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8db37-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8db37-105">Ten temat zawiera przykładowy kod, który przedstawia sposób implementowania dostawcy automatyzacji interfejsu użytkownika po stronie klienta w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8db37-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="8db37-106">Jest to rzadko scenariusz.</span><span class="sxs-lookup"><span data-stu-id="8db37-106">This is an uncommon scenario.</span></span> <span data-ttu-id="8db37-107">W większości przypadków aplikacji klienckiej automatyzacji interfejsu użytkownika używa dostawcy po stronie serwera lub dostawcy po stronie klienta, które znajdują się w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="8db37-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8db37-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="8db37-108">Example</span></span>  
 <span data-ttu-id="8db37-109">Poniższy przykładowy kod implementuje prostego dostawcy dla okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="8db37-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="8db37-110">Ten kod nie ma żadnych przydatne funkcje, ale jest jedynie do zademonstrowania podstawowe kroki konfigurowania dostawcy kodem klienta i rejestrując ją za pomocą <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span><span class="sxs-lookup"><span data-stu-id="8db37-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="8db37-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8db37-111">See Also</span></span>  
 [<span data-ttu-id="8db37-112">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8db37-112">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="8db37-113">Rejestrowanie zestawów dostawcy po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="8db37-113">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)  
 [<span data-ttu-id="8db37-114">Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="8db37-114">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [<span data-ttu-id="8db37-115">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="8db37-115">Client-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
