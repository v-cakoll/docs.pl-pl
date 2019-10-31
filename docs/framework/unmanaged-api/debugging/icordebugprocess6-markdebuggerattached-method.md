---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: 48bab20a71144b28f24951556eb36210d7b6aebf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123430"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="d0300-102">Metoda ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="d0300-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="d0300-103">Zmienia wewnętrzny stan debugee, tak aby Metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> w .NET Frameworkej bibliotece klas zwracała `true`.</span><span class="sxs-lookup"><span data-stu-id="d0300-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0300-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0300-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0300-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0300-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="d0300-106">`true`, jeśli metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> powinna wskazywać, że debuger jest dołączony; `false` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="d0300-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0300-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0300-107">Return Value</span></span>  
 <span data-ttu-id="d0300-108">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d0300-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="d0300-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0300-109">Return value</span></span>|<span data-ttu-id="d0300-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d0300-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="d0300-111">Pomyślnie Zaktualizowano debugowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d0300-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="d0300-112">Zestaw, który zawiera metodę <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>, nie został załadowany lub jakiś inny błąd, taki jak brakujące metadane, uniemożliwia jego rozpoznanie.</span><span class="sxs-lookup"><span data-stu-id="d0300-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="d0300-113">Ten błąd jest typowy i niegroźny.</span><span class="sxs-lookup"><span data-stu-id="d0300-113">This error is common and benign.</span></span> <span data-ttu-id="d0300-114">Należy wywołać metodę ponownie, gdy dodatkowe zestawy są ładowane.</span><span class="sxs-lookup"><span data-stu-id="d0300-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="d0300-115">Inne błędne wartości `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d0300-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="d0300-116">Inne wartości najkorzystnie wskazują debuger błędna lub składniki kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d0300-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0300-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0300-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0300-118">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d0300-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0300-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0300-119">Requirements</span></span>  
 <span data-ttu-id="d0300-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0300-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0300-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0300-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0300-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d0300-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0300-123">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0300-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0300-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0300-124">See also</span></span>

- [<span data-ttu-id="d0300-125">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0300-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="d0300-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0300-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
