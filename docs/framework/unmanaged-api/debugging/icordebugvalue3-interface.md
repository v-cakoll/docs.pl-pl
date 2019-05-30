---
title: ICorDebugValue3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4bf3605331e6900fd890e49bb3f71f4ca4409c7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377595"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="adc1d-102">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="adc1d-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="adc1d-103">Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic, które są większe niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="adc1d-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="adc1d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="adc1d-104">Methods</span></span>  
  
|<span data-ttu-id="adc1d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="adc1d-105">Method</span></span>|<span data-ttu-id="adc1d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="adc1d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adc1d-107">GetSize64, metoda</span><span class="sxs-lookup"><span data-stu-id="adc1d-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="adc1d-108">Pobiera rozmiar w bajtach to `ICorDebugValue3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="adc1d-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adc1d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="adc1d-109">Remarks</span></span>  
 <span data-ttu-id="adc1d-110">[ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metoda zwraca rozmiar obiektu, z zakresu od 0 do 2 147 483 647 bajtów.</span><span class="sxs-lookup"><span data-stu-id="adc1d-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="adc1d-111">W .NET Framework 4.5 rozmiar macierzy może przekraczać 2 GB.</span><span class="sxs-lookup"><span data-stu-id="adc1d-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="adc1d-112">`ICorDebugValue3` Interfejsu pozwala określić rozmiar macierzy.</span><span class="sxs-lookup"><span data-stu-id="adc1d-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adc1d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="adc1d-113">Requirements</span></span>  
 <span data-ttu-id="adc1d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adc1d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc1d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="adc1d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adc1d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adc1d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adc1d-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc1d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc1d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adc1d-118">See also</span></span>

- [<span data-ttu-id="adc1d-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="adc1d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="adc1d-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="adc1d-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
