---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e2e94ac4e30fbdb375175148a5b448c51821f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128027"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="d1839-102">Metoda ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="d1839-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="d1839-103">Zmienia stan wewnętrzny debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> zwraca metody w bibliotece klas programu .NET Framework `true`.</span><span class="sxs-lookup"><span data-stu-id="d1839-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1839-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1839-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1839-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1839-105">Parameters</span></span>  
 `fIsAttached`  
 `true` <span data-ttu-id="d1839-106">Jeśli <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metody powinny wskazywać, że jest dołączony debuger; `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="d1839-106">if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1839-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1839-107">Return Value</span></span>  
 <span data-ttu-id="d1839-108">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d1839-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="d1839-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1839-109">Return value</span></span>|<span data-ttu-id="d1839-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d1839-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="d1839-111">Pomyślnie zaktualizowano debugowany program.</span><span class="sxs-lookup"><span data-stu-id="d1839-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="d1839-112">Zestaw, który zawiera <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda nie jest załadowany lub inny błąd, takie jak Brak metadanych uniemożliwia jej rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="d1839-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="d1839-113">Ten błąd jest najczęściej i niegroźne.</span><span class="sxs-lookup"><span data-stu-id="d1839-113">This error is common and benign.</span></span> <span data-ttu-id="d1839-114">Należy wywołać metodę ponownie, gdy załadować dodatkowe zestawy.</span><span class="sxs-lookup"><span data-stu-id="d1839-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="d1839-115">Inne niepowodzenia `HRESULT` wartości.</span><span class="sxs-lookup"><span data-stu-id="d1839-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="d1839-116">Inne wartości, które mogą wskazywać nieprawidłowo funkcjonującego debugera lub składniki kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d1839-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1839-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1839-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1839-118">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d1839-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1839-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1839-119">Requirements</span></span>  
 <span data-ttu-id="d1839-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1839-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1839-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1839-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1839-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1839-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d1839-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d1839-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d1839-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1839-124">See also</span></span>

- [<span data-ttu-id="d1839-125">Interfejs ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="d1839-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="d1839-126">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d1839-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
