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
ms.openlocfilehash: 9f521eb942f37b8cf1d00bcc672071a69692b876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396647"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="197a3-102">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="197a3-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="197a3-103">Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic o rozmiarze większym niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="197a3-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="197a3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="197a3-104">Methods</span></span>  
  
|<span data-ttu-id="197a3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="197a3-105">Method</span></span>|<span data-ttu-id="197a3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="197a3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="197a3-107">GetSize64, metoda</span><span class="sxs-lookup"><span data-stu-id="197a3-107">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="197a3-108">Pobiera rozmiar tego obiektu w bajtach `ICorDebugValue3` .</span><span class="sxs-lookup"><span data-stu-id="197a3-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="197a3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="197a3-109">Remarks</span></span>  
 <span data-ttu-id="197a3-110">Metoda [ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) zwraca rozmiar obiektu, który mieści się w zakresie od 0 do 2 147 483 647 bajtów.</span><span class="sxs-lookup"><span data-stu-id="197a3-110">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="197a3-111">W .NET Framework 4,5 rozmiar tablic może przekroczyć 2 GB.</span><span class="sxs-lookup"><span data-stu-id="197a3-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="197a3-112">`ICorDebugValue3`Interfejs umożliwia określenie rozmiaru tych tablic.</span><span class="sxs-lookup"><span data-stu-id="197a3-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="197a3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="197a3-113">Requirements</span></span>  
 <span data-ttu-id="197a3-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="197a3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="197a3-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="197a3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="197a3-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="197a3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="197a3-117">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="197a3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197a3-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="197a3-118">See also</span></span>

- [<span data-ttu-id="197a3-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="197a3-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="197a3-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="197a3-120">Debugging</span></span>](index.md)
