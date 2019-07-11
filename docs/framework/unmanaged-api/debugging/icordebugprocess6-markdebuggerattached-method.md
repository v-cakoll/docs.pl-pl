---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f21ea449cf30bd9c07b7ae9b382877ce18f102d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736416"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="6fb35-102">Metoda ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="6fb35-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="6fb35-103">Zmienia stan wewnętrzny debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> zwraca metody w bibliotece klas programu .NET Framework `true`.</span><span class="sxs-lookup"><span data-stu-id="6fb35-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fb35-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fb35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fb35-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="6fb35-106">`true` Jeśli <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metody powinny wskazywać, że jest dołączony debuger; `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="6fb35-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fb35-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6fb35-107">Return Value</span></span>  
 <span data-ttu-id="6fb35-108">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6fb35-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="6fb35-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6fb35-109">Return value</span></span>|<span data-ttu-id="6fb35-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6fb35-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="6fb35-111">Pomyślnie zaktualizowano debugowany program.</span><span class="sxs-lookup"><span data-stu-id="6fb35-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="6fb35-112">Zestaw, który zawiera <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda nie jest załadowany lub inny błąd, takie jak Brak metadanych uniemożliwia jej rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="6fb35-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="6fb35-113">Ten błąd jest najczęściej i niegroźne.</span><span class="sxs-lookup"><span data-stu-id="6fb35-113">This error is common and benign.</span></span> <span data-ttu-id="6fb35-114">Należy wywołać metodę ponownie, gdy załadować dodatkowe zestawy.</span><span class="sxs-lookup"><span data-stu-id="6fb35-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="6fb35-115">Inne niepowodzenia `HRESULT` wartości.</span><span class="sxs-lookup"><span data-stu-id="6fb35-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="6fb35-116">Inne wartości, które mogą wskazywać nieprawidłowo funkcjonującego debugera lub składniki kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6fb35-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fb35-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fb35-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fb35-118">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6fb35-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb35-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fb35-119">Requirements</span></span>  
 <span data-ttu-id="6fb35-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fb35-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb35-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fb35-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fb35-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fb35-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fb35-123">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb35-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb35-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fb35-124">See also</span></span>

- [<span data-ttu-id="6fb35-125">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fb35-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="6fb35-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6fb35-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
