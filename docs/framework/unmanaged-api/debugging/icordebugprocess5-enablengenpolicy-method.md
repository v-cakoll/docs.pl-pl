---
title: ICorDebugProcess5::EnableNGENPolicy — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: 9497bea9b7cc5eb98876c923858dbcbc6adf9d07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792450"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="129a5-102">ICorDebugProcess5::EnableNGENPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="129a5-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="129a5-103">Ustawia wartość określającą sposób ładowania obrazów natywnych przez aplikację podczas działania w ramach zarządzanego debugera.</span><span class="sxs-lookup"><span data-stu-id="129a5-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="129a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="129a5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="129a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="129a5-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="129a5-106">podczas Stała [CorDebugNGenPolicy —](cordebugngenpolicy-enumeration.md) , która określa, w jaki sposób aplikacja ładuje obrazy natywne podczas działania w zarządzanym debugerze.</span><span class="sxs-lookup"><span data-stu-id="129a5-106">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="129a5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="129a5-107">Remarks</span></span>  
 <span data-ttu-id="129a5-108">Jeśli zasady zostały ustawione pomyślnie, metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="129a5-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="129a5-109">Jeśli `ePolicy` znajduje się poza zakresem wartości wyliczanych zdefiniowanych przez [CorDebugNGenPolicy —](cordebugngenpolicy-enumeration.md), metoda zwraca `E_INVALIDARG` i wywołanie metody nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="129a5-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="129a5-110">Jeśli nie można zaktualizować zasad generatora obrazów natywnych (Ngen. exe), metoda zwraca `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="129a5-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="129a5-111">Metodę `ICorDebugProcess5::EnableNGenPolicy` można wywołać w dowolnym momencie w okresie istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="129a5-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="129a5-112">Zasady obowiązują dla wszystkich modułów, które są ładowane po ustawieniu zasad.</span><span class="sxs-lookup"><span data-stu-id="129a5-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="129a5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="129a5-113">Requirements</span></span>  
 <span data-ttu-id="129a5-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="129a5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="129a5-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="129a5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="129a5-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="129a5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="129a5-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="129a5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="129a5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="129a5-118">See also</span></span>

- [<span data-ttu-id="129a5-119">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="129a5-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="129a5-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="129a5-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="129a5-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="129a5-121">Debugging</span></span>](index.md)
