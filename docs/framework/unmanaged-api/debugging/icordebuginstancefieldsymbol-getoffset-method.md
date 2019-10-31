---
title: 'ICorDebugInstanceFieldSymbol:: GetOffset — Metoda'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 3886e29a1c2fd44fbe50d1eef722f99da7abdbe5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139015"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="66003-102">ICorDebugInstanceFieldSymbol:: GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="66003-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="66003-103">Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="66003-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66003-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66003-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66003-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66003-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="66003-106">Wskaźnik do liczby bajtów, które to pole wystąpienia jest przesunięte w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="66003-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66003-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66003-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66003-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="66003-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66003-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66003-109">Requirements</span></span>  
 <span data-ttu-id="66003-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66003-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66003-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66003-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66003-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66003-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66003-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66003-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66003-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66003-114">See also</span></span>

- [<span data-ttu-id="66003-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="66003-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="66003-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="66003-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
