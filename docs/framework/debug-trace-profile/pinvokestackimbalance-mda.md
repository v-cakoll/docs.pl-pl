---
title: pInvokeStackImbalance MDA
description: Zapoznaj się z PInvokeStackImbalance MDA, który może być aktywowany podczas naruszenia zasad dostępu lub uszkodzenia pamięci podczas tworzenia lub wykonywania wywołania platformy.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
ms.openlocfilehash: 89afd3fce3f2a8bffe88d45991ceeb59fc5e5b76
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803667"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="fbec4-103">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="fbec4-103">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="fbec4-104">`PInvokeStackImbalance`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko CLR wykryje, że głębokość stosu po wywołaniu wywołania platformy nie jest zgodna z oczekiwaną głębokością stosu, z uwzględnieniem konwencji wywoływania określonej w <xref:System.Runtime.InteropServices.DllImportAttribute> atrybucie i deklaracji parametrów w zarządzanym podpisie.</span><span class="sxs-lookup"><span data-stu-id="fbec4-104">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="fbec4-105">`PInvokeStackImbalance`Zdarzenie MDA jest implementowane tylko dla 32-bitowych platform x86.</span><span class="sxs-lookup"><span data-stu-id="fbec4-105">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="fbec4-106">`PInvokeStackImbalance`Zdarzenie MDA jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="fbec4-106">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="fbec4-107">W programie Visual Studio 2017 i nowszych wersjach, `PInvokeStackImbalance` zdarzenie MDA pojawia się na liście **asystentów debugowania zarządzanego** w oknie dialogowym **Ustawienia wyjątku** (które jest wyświetlane po wybraniu opcji **Debuguj**  >  **Windows**  >  **Ustawienia wyjątków**systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="fbec4-107">In Visual Studio 2017 and later versions, the `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="fbec4-108">Jednak zaznaczenie lub wyczyszczenie pola wyboru **Przerwij, gdy zostało zgłoszone** , nie powoduje włączenia ani wyłączenia MDA; kontroluje tylko, czy program Visual Studio zgłasza wyjątek podczas aktywowania MDA.</span><span class="sxs-lookup"><span data-stu-id="fbec4-108">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="fbec4-109">Objawy</span><span class="sxs-lookup"><span data-stu-id="fbec4-109">Symptoms</span></span>

<span data-ttu-id="fbec4-110">Aplikacja napotyka naruszenie zasad dostępu lub uszkodzenie pamięci podczas wykonywania lub po wywołaniu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="fbec4-110">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="fbec4-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="fbec4-111">Cause</span></span>

<span data-ttu-id="fbec4-112">Zarządzany podpis wywołania wywołania platformy może być niezgodny z niezarządzanym podpisem wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="fbec4-112">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="fbec4-113">Niezgodność może być spowodowana przez zarządzaną sygnaturę, która nie deklaruje poprawnej liczby parametrów lub nie określa odpowiedniego rozmiaru parametrów.</span><span class="sxs-lookup"><span data-stu-id="fbec4-113">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="fbec4-114">Zdarzenie MDA można również uaktywnić, ponieważ Konwencja wywoływania, prawdopodobnie określona przez <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut, nie jest zgodna z niezarządzaną konwencją wywoływania.</span><span class="sxs-lookup"><span data-stu-id="fbec4-114">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="fbec4-115">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="fbec4-115">Resolution</span></span>

<span data-ttu-id="fbec4-116">Przejrzyj sygnaturę wywołania i konwencję wywoływania zarządzanej platformy, aby potwierdzić, że jest zgodna z sygnaturą i konwencją wywoływania natywnego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fbec4-116">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="fbec4-117">Spróbuj jawnie określić konwencję wywoływania zarówno dla stron zarządzanych, jak i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="fbec4-117">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="fbec4-118">Istnieje również możliwość, chociaż nie jest to prawdopodobne, że niezarządzana funkcja nierównoważy stos z innego powodu, na przykład błąd w kompilatorze niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="fbec4-118">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="fbec4-119">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="fbec4-119">Effect on the Runtime</span></span>

<span data-ttu-id="fbec4-120">Wymusza, aby wszystkie wywołania wywoływane przez platformę przejmowanie niezoptymalizowanej ścieżki w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="fbec4-120">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="fbec4-121">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="fbec4-121">Output</span></span>

<span data-ttu-id="fbec4-122">Komunikat MDA zawiera nazwę wywołania metody wywoływanej przez platformę, która powoduje Niezrównoważenie stosu.</span><span class="sxs-lookup"><span data-stu-id="fbec4-122">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="fbec4-123">Przykładowy komunikat wywołującego wywołanie metody `SampleMethod` jest:</span><span class="sxs-lookup"><span data-stu-id="fbec4-123">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="fbec4-124">**Wywołanie funkcji PInvoke "SampleMethod" ma niezrównoważony stos. Prawdopodobnie jest to spowodowane tym, że zarządzana sygnatura PInvoke nie jest zgodna z niezarządzanym podpisem docelowym. Sprawdź, czy Konwencja wywoływania i parametry sygnatury PInvoke pasują do docelowego podpisu niezarządzanego.**</span><span class="sxs-lookup"><span data-stu-id="fbec4-124">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="fbec4-125">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="fbec4-125">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="fbec4-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbec4-126">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="fbec4-127">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="fbec4-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="fbec4-128">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="fbec4-128">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
