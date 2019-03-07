---
title: ICorDebugInstanceFieldSymbol::GetOffset Method
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a88de396d946c37b30688ab614d2bcc549c86873
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468133"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="587cc-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span><span class="sxs-lookup"><span data-stu-id="587cc-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="587cc-103">Pobiera przesunięcie w bajtach tego pola wystąpienia w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="587cc-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="587cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="587cc-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="587cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="587cc-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="587cc-106">Wskaźnik do liczby bajtów, że to wystąpienie pole jest przesuwane w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="587cc-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="587cc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="587cc-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="587cc-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="587cc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="587cc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="587cc-109">Requirements</span></span>  
 <span data-ttu-id="587cc-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="587cc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="587cc-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="587cc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="587cc-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="587cc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="587cc-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="587cc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587cc-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="587cc-114">See also</span></span>
- [<span data-ttu-id="587cc-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="587cc-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="587cc-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="587cc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
