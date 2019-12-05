---
title: pInvokeStackImbalance MDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 117e0838f78d43bf9ffa555947bf8749830c9840
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801994"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="a8af5-102">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="a8af5-102">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="a8af5-103">Asystent debugowania zarządzanego `PInvokeStackImbalance` (MDA) jest uaktywniany, gdy środowisko CLR wykryje, że głębokość stosu po wywołaniu wywołania platformy jest niezgodna z oczekiwaną głębokością stosu, w przypadku konwencji wywoływania określonej w atrybucie <xref:System.Runtime.InteropServices.DllImportAttribute> i deklaracji parametrów w zarządzanym podpisie.</span><span class="sxs-lookup"><span data-stu-id="a8af5-103">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="a8af5-104">`PInvokeStackImbalance` MDA jest implementowana tylko dla 32-bitowych platform x86.</span><span class="sxs-lookup"><span data-stu-id="a8af5-104">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="a8af5-105">`PInvokeStackImbalance` MDA jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="a8af5-105">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="a8af5-106">W programie Visual Studio 2017 i nowszych wersjach `PInvokeStackImbalance` MDA pojawia się na liście **asystentów debugowania zarządzanego** w oknie dialogowym **Ustawienia wyjątku** (wyświetlanym po wybraniu opcji **Debuguj** > **Windows** > **Ustawienia wyjątku**).</span><span class="sxs-lookup"><span data-stu-id="a8af5-106">In Visual Studio 2017 and later versions, the `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="a8af5-107">Jednak zaznaczenie lub wyczyszczenie pola wyboru **Przerwij, gdy zostało zgłoszone** , nie powoduje włączenia ani wyłączenia MDA; kontroluje tylko, czy program Visual Studio zgłasza wyjątek podczas aktywowania MDA.</span><span class="sxs-lookup"><span data-stu-id="a8af5-107">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="a8af5-108">Symptomy</span><span class="sxs-lookup"><span data-stu-id="a8af5-108">Symptoms</span></span>

<span data-ttu-id="a8af5-109">Aplikacja napotyka naruszenie zasad dostępu lub uszkodzenie pamięci podczas wykonywania lub po wywołaniu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="a8af5-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="a8af5-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a8af5-110">Cause</span></span>

<span data-ttu-id="a8af5-111">Zarządzany podpis wywołania wywołania platformy może być niezgodny z niezarządzanym podpisem wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="a8af5-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="a8af5-112">Niezgodność może być spowodowana przez zarządzaną sygnaturę, która nie deklaruje poprawnej liczby parametrów lub nie określa odpowiedniego rozmiaru parametrów.</span><span class="sxs-lookup"><span data-stu-id="a8af5-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="a8af5-113">Zdarzenie MDA można również uaktywnić, ponieważ Konwencja wywoływania, prawdopodobnie określona przez atrybut <xref:System.Runtime.InteropServices.DllImportAttribute>, nie jest zgodna z niezarządzaną konwencją wywoływania.</span><span class="sxs-lookup"><span data-stu-id="a8af5-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="a8af5-114">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a8af5-114">Resolution</span></span>

<span data-ttu-id="a8af5-115">Przejrzyj sygnaturę wywołania i konwencję wywoływania zarządzanej platformy, aby potwierdzić, że jest zgodna z sygnaturą i konwencją wywoływania natywnego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a8af5-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="a8af5-116">Spróbuj jawnie określić konwencję wywoływania zarówno dla stron zarządzanych, jak i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="a8af5-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="a8af5-117">Istnieje również możliwość, chociaż nie jest to prawdopodobne, że niezarządzana funkcja nierównoważy stos z innego powodu, na przykład błąd w kompilatorze niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="a8af5-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="a8af5-118">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a8af5-118">Effect on the Runtime</span></span>

<span data-ttu-id="a8af5-119">Wymusza, aby wszystkie wywołania wywoływane przez platformę przejmowanie niezoptymalizowanej ścieżki w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="a8af5-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="a8af5-120">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a8af5-120">Output</span></span>

<span data-ttu-id="a8af5-121">Komunikat MDA zawiera nazwę wywołania metody wywoływanej przez platformę, która powoduje Niezrównoważenie stosu.</span><span class="sxs-lookup"><span data-stu-id="a8af5-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="a8af5-122">Przykładowy komunikat o wywołaniu wywołania platformy dla metody `SampleMethod` to:</span><span class="sxs-lookup"><span data-stu-id="a8af5-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="a8af5-123">**Wywołanie funkcji PInvoke "SampleMethod" ma niezrównoważony stos. Prawdopodobnie jest to spowodowane tym, że zarządzana sygnatura PInvoke nie jest zgodna z niezarządzanym podpisem docelowym. Sprawdź, czy Konwencja wywoływania i parametry sygnatury PInvoke pasują do docelowego podpisu niezarządzanego.**</span><span class="sxs-lookup"><span data-stu-id="a8af5-123">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="a8af5-124">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a8af5-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="a8af5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8af5-125">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a8af5-126">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a8af5-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a8af5-127">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="a8af5-127">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
