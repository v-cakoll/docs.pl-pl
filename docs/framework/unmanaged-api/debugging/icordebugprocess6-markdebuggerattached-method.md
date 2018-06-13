---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aea837c4973f7a0c157a36c05799536ab528638e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421021"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="2dc37-102">Metoda ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="2dc37-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="2dc37-103">Wewnętrzny stan klasy obiektu debugowanego zmiany, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda w bibliotece klas programu .NET Framework zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="2dc37-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2dc37-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2dc37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2dc37-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="2dc37-106">`true` Jeśli <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metody powinny wskazywać, że jest dołączony debuger; `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="2dc37-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dc37-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2dc37-107">Return Value</span></span>  
 <span data-ttu-id="2dc37-108">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2dc37-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="2dc37-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2dc37-109">Return value</span></span>|<span data-ttu-id="2dc37-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2dc37-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="2dc37-111">Obiekt debugowany został pomyślnie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="2dc37-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="2dc37-112">Zestaw zawierający <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> — metoda nie jest załadowany lub inny błąd, takie jak Brak metadanych uniemożliwia jego rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="2dc37-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="2dc37-113">Ten błąd jest typowe i niegroźne.</span><span class="sxs-lookup"><span data-stu-id="2dc37-113">This error is common and benign.</span></span> <span data-ttu-id="2dc37-114">Należy wywołać metodę ponownie, gdy załadować następującej liczby dodatkowych zestawów.</span><span class="sxs-lookup"><span data-stu-id="2dc37-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="2dc37-115">Inne niepowodzenie `HRESULT` wartości.</span><span class="sxs-lookup"><span data-stu-id="2dc37-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="2dc37-116">Inne wartości, które mogą wskazywać błędna debugera lub składników kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2dc37-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dc37-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2dc37-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2dc37-118">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2dc37-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dc37-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2dc37-119">Requirements</span></span>  
 <span data-ttu-id="2dc37-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dc37-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dc37-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2dc37-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2dc37-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2dc37-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2dc37-123">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dc37-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc37-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2dc37-124">See Also</span></span>  
 [<span data-ttu-id="2dc37-125">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="2dc37-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="2dc37-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2dc37-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
