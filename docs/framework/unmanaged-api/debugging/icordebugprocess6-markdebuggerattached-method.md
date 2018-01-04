---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d3d47f3b5ce6912d5a58f79117b6cd2e05d3ecd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="b9b66-102">Metoda ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="b9b66-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="b9b66-103">Wewnętrzny stan klasy obiektu debugowanego zmiany, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda w bibliotece klas programu .NET Framework zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="b9b66-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9b66-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9b66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9b66-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="b9b66-106">`true`Jeśli <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metody powinny wskazywać, że jest dołączony debuger; `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="b9b66-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9b66-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b9b66-107">Return Value</span></span>  
 <span data-ttu-id="b9b66-108">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b9b66-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="b9b66-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b9b66-109">Return value</span></span>|<span data-ttu-id="b9b66-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b66-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9b66-111">Obiekt debugowany został pomyślnie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="b9b66-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="b9b66-112">Zestaw zawierający <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> — metoda nie jest załadowany lub inny błąd, takie jak Brak metadanych uniemożliwia jego rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="b9b66-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="b9b66-113">Ten błąd jest typowe i niegroźne.</span><span class="sxs-lookup"><span data-stu-id="b9b66-113">This error is common and benign.</span></span> <span data-ttu-id="b9b66-114">Należy wywołać metodę ponownie, gdy załadować następującej liczby dodatkowych zestawów.</span><span class="sxs-lookup"><span data-stu-id="b9b66-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="b9b66-115">Inne niepowodzenie `HRESULT` wartości.</span><span class="sxs-lookup"><span data-stu-id="b9b66-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="b9b66-116">Inne wartości, które mogą wskazywać błędna debugera lub składników kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b9b66-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9b66-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9b66-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9b66-118">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b9b66-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b66-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9b66-119">Requirements</span></span>  
 <span data-ttu-id="b9b66-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9b66-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b66-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9b66-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9b66-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9b66-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9b66-123">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b66-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b66-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b66-124">See Also</span></span>  
 [<span data-ttu-id="b9b66-125">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9b66-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="b9b66-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b9b66-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
