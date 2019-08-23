---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c818b196f3252138f2a9c601b04f1d7a6727bc6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912740"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="ac294-102">Metoda ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="ac294-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="ac294-103">Zmienia wewnętrzny stan debugee, tak aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> Metoda w bibliotece klas .NET Framework zwracana. `true`</span><span class="sxs-lookup"><span data-stu-id="ac294-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac294-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac294-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac294-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac294-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="ac294-106">`true`<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> Jeśli metoda powinna wskazywać, że debuger jest dołączony; `false` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="ac294-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac294-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ac294-107">Return Value</span></span>  
 <span data-ttu-id="ac294-108">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ac294-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="ac294-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ac294-109">Return value</span></span>|<span data-ttu-id="ac294-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ac294-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="ac294-111">Pomyślnie Zaktualizowano debugowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ac294-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="ac294-112">Zestaw, który zawiera <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metodę, nie został załadowany lub jakiś inny błąd, taki jak brakujące metadane, uniemożliwia jego rozpoznanie.</span><span class="sxs-lookup"><span data-stu-id="ac294-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="ac294-113">Ten błąd jest typowy i niegroźny.</span><span class="sxs-lookup"><span data-stu-id="ac294-113">This error is common and benign.</span></span> <span data-ttu-id="ac294-114">Należy wywołać metodę ponownie, gdy dodatkowe zestawy są ładowane.</span><span class="sxs-lookup"><span data-stu-id="ac294-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="ac294-115">Inne błędne `HRESULT` wartości.</span><span class="sxs-lookup"><span data-stu-id="ac294-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="ac294-116">Inne wartości najkorzystnie wskazują debuger błędna lub składniki kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ac294-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac294-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac294-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac294-118">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ac294-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac294-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac294-119">Requirements</span></span>  
 <span data-ttu-id="ac294-120">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac294-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac294-121">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac294-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac294-122">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac294-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac294-123">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac294-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac294-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac294-124">See also</span></span>

- [<span data-ttu-id="ac294-125">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac294-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="ac294-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ac294-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
