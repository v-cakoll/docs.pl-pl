---
title: invalidMemberDeclaration MDA
description: Zapoznaj się z asystentem debugowania zarządzanego przez invalidMemberDeclaration, który jest wywoływany w przypadku zwrócenia błędu HRESULT do modelu COM bez wywoływania metody zarządzanej.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 5dbfba2baec3263d91746c06379438e97a81f005
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051717"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="f5d09-103">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="f5d09-103">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="f5d09-104">`invalidMemberDeclaration`Asystent debugowania zarządzanego (MDA) został aktywowany, aby zgłosić błąd, który występuje podczas określania sposobu organizowania parametrów elementu członkowskiego, który ma być wywoływany z modelu com.</span><span class="sxs-lookup"><span data-stu-id="f5d09-104">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f5d09-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="f5d09-105">Symptoms</span></span>  
 <span data-ttu-id="f5d09-106">Błąd HRESULT jest zwracany do modelu COM bez wywołania metody zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="f5d09-106">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f5d09-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f5d09-107">Cause</span></span>  
 <span data-ttu-id="f5d09-108">Najprawdopodobniej ze względu na niezgodny <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut na jednym z parametrów.</span><span class="sxs-lookup"><span data-stu-id="f5d09-108">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f5d09-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f5d09-109">Resolution</span></span>  
 <span data-ttu-id="f5d09-110">Określ prawidłowe <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybuty dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="f5d09-110">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f5d09-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f5d09-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="f5d09-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="f5d09-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f5d09-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f5d09-113">Output</span></span>  
 <span data-ttu-id="f5d09-114">Komunikat informacyjny zawierający nazwę elementu członkowskiego, nazwę typu i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="f5d09-114">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f5d09-115">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="f5d09-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5d09-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5d09-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f5d09-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f5d09-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f5d09-118">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="f5d09-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
