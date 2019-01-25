---
title: invalidMemberDeclaration MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c276df65497a0d8cafea80959b8193790c19ebba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667352"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="5bafe-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="5bafe-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="5bafe-103">`invalidMemberDeclaration` Zarządzanego Asystenta debugowania (MDA) jest aktywowana Aby zgłosić błąd występujący podczas określania sposobu organizowania parametrów elementu członkowskiego, wywoływana z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5bafe-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5bafe-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="5bafe-104">Symptoms</span></span>  
 <span data-ttu-id="5bafe-105">Błąd HRESULT jest zwracana do COM bez zarządzanej metody o została wywołana.</span><span class="sxs-lookup"><span data-stu-id="5bafe-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5bafe-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="5bafe-106">Cause</span></span>  
 <span data-ttu-id="5bafe-107">Jest to najprawdopodobniej z powodu niezgodnej <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu na jeden z parametrów.</span><span class="sxs-lookup"><span data-stu-id="5bafe-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5bafe-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="5bafe-108">Resolution</span></span>  
 <span data-ttu-id="5bafe-109">Określ prawidłowy <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybuty w parametrach.</span><span class="sxs-lookup"><span data-stu-id="5bafe-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5bafe-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5bafe-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="5bafe-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="5bafe-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5bafe-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="5bafe-112">Output</span></span>  
 <span data-ttu-id="5bafe-113">Komunikat informacyjny zawierające nazwy elementu członkowskiego, wpisz nazwę i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="5bafe-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5bafe-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bafe-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bafe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bafe-115">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5bafe-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="5bafe-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5bafe-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="5bafe-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
