---
title: ICorDebugValue3::GetSize64 — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c016c9dbe27f77b48c65fcd24ac9e13a9d07ed3f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485460"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="25205-102">ICorDebugValue3::GetSize64 — Metoda</span><span class="sxs-lookup"><span data-stu-id="25205-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="25205-103">Pobiera rozmiar w bajtach to [icordebugvalue3 —](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="25205-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25205-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25205-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25205-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25205-105">Parameters</span></span>  
 <span data-ttu-id="25205-106">pSize</span><span class="sxs-lookup"><span data-stu-id="25205-106">pSize</span></span>  
 <span data-ttu-id="25205-107">[out] Wskaźnik do rozmiaru, w bajtach, tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="25205-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25205-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25205-108">Remarks</span></span>  
 <span data-ttu-id="25205-109">Jeśli ta wartość typ jest typem referencyjnym, ta metoda zwraca rozmiar wskaźnika, a nie rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="25205-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="25205-110">`ICorDebugValue3::GetSize` Metoda różni się od [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) metoda w typie jako parametr wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="25205-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="25205-111">W [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), parametr wyjściowy jest `ULONG32`; w `ICorDebugValue3::GetSize`, jest `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="25205-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="25205-112">Dzięki temu [icordebugvalue3 —](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interfejsu, aby zgłosić rozmiar tablic, które przekracza 2 GB.</span><span class="sxs-lookup"><span data-stu-id="25205-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25205-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25205-113">Requirements</span></span>  
 <span data-ttu-id="25205-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25205-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25205-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25205-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25205-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25205-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25205-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25205-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25205-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25205-118">See also</span></span>
- [<span data-ttu-id="25205-119">ICorDebugValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="25205-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="25205-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="25205-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
