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
ms.openlocfilehash: 5fa042223e47961dad0a6799ab8ca999ef76e285
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791093"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="20603-102">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="20603-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="20603-103">Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic o rozmiarze większym niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="20603-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20603-104">Metody</span><span class="sxs-lookup"><span data-stu-id="20603-104">Methods</span></span>  
  
|<span data-ttu-id="20603-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="20603-105">Method</span></span>|<span data-ttu-id="20603-106">Opis</span><span class="sxs-lookup"><span data-stu-id="20603-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20603-107">GetSize64, metoda</span><span class="sxs-lookup"><span data-stu-id="20603-107">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="20603-108">Pobiera rozmiar (w bajtach) tego obiektu `ICorDebugValue3`.</span><span class="sxs-lookup"><span data-stu-id="20603-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20603-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20603-109">Remarks</span></span>  
 <span data-ttu-id="20603-110">Metoda [ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) zwraca rozmiar obiektu, który mieści się w zakresie od 0 do 2 147 483 647 bajtów.</span><span class="sxs-lookup"><span data-stu-id="20603-110">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="20603-111">W .NET Framework 4,5 rozmiar tablic może przekroczyć 2 GB.</span><span class="sxs-lookup"><span data-stu-id="20603-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="20603-112">Interfejs `ICorDebugValue3` umożliwia określenie rozmiaru tych tablic.</span><span class="sxs-lookup"><span data-stu-id="20603-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20603-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20603-113">Requirements</span></span>  
 <span data-ttu-id="20603-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20603-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20603-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20603-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20603-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20603-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20603-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20603-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20603-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20603-118">See also</span></span>

- [<span data-ttu-id="20603-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="20603-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="20603-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="20603-120">Debugging</span></span>](index.md)
