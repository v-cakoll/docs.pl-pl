---
title: ICorDebugInstanceFieldSymbol::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0901e64a7da7f68b2fbcdb63636503893263435f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413793"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="57759-102">ICorDebugInstanceFieldSymbol::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="57759-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="57759-103">Pobiera rozmiar w bajtach pole wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="57759-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57759-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57759-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57759-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57759-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="57759-106">[out] Wskaźnik do długość pola.</span><span class="sxs-lookup"><span data-stu-id="57759-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57759-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57759-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57759-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="57759-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57759-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57759-109">Requirements</span></span>  
 <span data-ttu-id="57759-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57759-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57759-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57759-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57759-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57759-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57759-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57759-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57759-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57759-114">See Also</span></span>  
 [<span data-ttu-id="57759-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="57759-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="57759-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="57759-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
