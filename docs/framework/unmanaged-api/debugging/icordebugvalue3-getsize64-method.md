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
ms.openlocfilehash: 6eb26de83a6cdce47477e6cb3dffd6a94d889975
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397022"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="461da-102">ICorDebugValue3::GetSize64 — Metoda</span><span class="sxs-lookup"><span data-stu-id="461da-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="461da-103">Pobiera rozmiar (w bajtach) tego obiektu [ICorDebugValue3](icordebugvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="461da-103">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="461da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="461da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="461da-105">Parameters</span></span>  
 <span data-ttu-id="461da-106">pSize</span><span class="sxs-lookup"><span data-stu-id="461da-106">pSize</span></span>  
 <span data-ttu-id="461da-107">określoną Wskaźnik do rozmiaru, w bajtach, tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="461da-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="461da-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="461da-108">Remarks</span></span>  
 <span data-ttu-id="461da-109">Jeśli typ tej wartości jest typem referencyjnym, Metoda ta zwraca rozmiar wskaźnika, a nie rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="461da-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="461da-110">`ICorDebugValue3::GetSize`Metoda różni się od metody [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) w typie parametru wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="461da-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="461da-111">W [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md)parametr wyjściowy to a `ULONG32` ; w `ICorDebugValue3::GetSize` , jest to `ULONG64` .</span><span class="sxs-lookup"><span data-stu-id="461da-111">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="461da-112">Dzięki temu Interfejs [ICorDebugValue3](icordebugvalue3-interface.md) może raportować rozmiar tablic, które przekraczają 2 GB.</span><span class="sxs-lookup"><span data-stu-id="461da-112">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="461da-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="461da-113">Requirements</span></span>  
 <span data-ttu-id="461da-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="461da-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="461da-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="461da-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="461da-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="461da-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="461da-117">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461da-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461da-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="461da-118">See also</span></span>

- [<span data-ttu-id="461da-119">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="461da-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="461da-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="461da-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
