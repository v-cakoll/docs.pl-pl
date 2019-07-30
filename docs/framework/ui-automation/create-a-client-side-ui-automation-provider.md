---
title: Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: 722b6db8a777f0e945b91fa7fa27db0dd2858d7b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629531"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="f762b-102">Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="f762b-102">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="f762b-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f762b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f762b-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f762b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f762b-105">Ten temat zawiera przykładowy kod pokazujący sposób implementacji dostawcy automatyzacji interfejsu użytkownika po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="f762b-105">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f762b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f762b-106">Example</span></span>  
 <span data-ttu-id="f762b-107">Poniższy przykładowy kod można utworzyć w bibliotece dołączanej dynamicznie (DLL), która implementuje bardzo prostego dostawcę po stronie klienta dla okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="f762b-107">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="f762b-108">Kod nie ma żadnych użytecznych funkcji, ale ma na celu przedstawienie podstawowych kroków konfiguracji zestawu dostawcy, który może być zarejestrowany przez aplikację klienta automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f762b-108">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="f762b-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f762b-109">See also</span></span>

- [<span data-ttu-id="f762b-110">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f762b-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="f762b-111">Rejestrowanie zestawów dostawcy po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="f762b-111">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
