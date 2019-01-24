---
title: ICorDebugInstanceFieldSymbol::GetSize Method
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04d866888c15585ff5058f870257b317ac888be7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696987"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="e7b46-102">ICorDebugInstanceFieldSymbol::GetSize Method</span><span class="sxs-lookup"><span data-stu-id="e7b46-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="e7b46-103">Pobiera rozmiar w bajtach pole wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7b46-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7b46-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7b46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7b46-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="e7b46-106">[out] Wskaźnik do długość pola.</span><span class="sxs-lookup"><span data-stu-id="e7b46-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7b46-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7b46-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7b46-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e7b46-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b46-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7b46-109">Requirements</span></span>  
 <span data-ttu-id="e7b46-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7b46-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b46-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7b46-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7b46-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7b46-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7b46-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b46-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b46-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7b46-114">See also</span></span>
- [<span data-ttu-id="e7b46-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7b46-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="e7b46-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e7b46-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
