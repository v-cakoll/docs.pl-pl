---
title: 'ICorDebugInstanceFieldSymbol:: GetOffset — Metoda'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 453f691f414050905f5d73e201ebeed79e2aaf50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910203"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="2641b-102">ICorDebugInstanceFieldSymbol:: GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="2641b-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="2641b-103">Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2641b-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2641b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2641b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2641b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2641b-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="2641b-106">Wskaźnik do liczby bajtów, które to pole wystąpienia jest przesunięte w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2641b-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2641b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2641b-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2641b-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2641b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2641b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2641b-109">Requirements</span></span>  
 <span data-ttu-id="2641b-110">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2641b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2641b-111">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2641b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2641b-112">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2641b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2641b-113">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2641b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2641b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2641b-114">See also</span></span>

- [<span data-ttu-id="2641b-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="2641b-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="2641b-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2641b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
