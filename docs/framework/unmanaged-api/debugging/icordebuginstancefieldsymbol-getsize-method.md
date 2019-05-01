---
title: ICorDebugInstanceFieldSymbol::GetSize Method
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc09de2120399dcfe309757d554e1de72e55f07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946376"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="5b308-102">ICorDebugInstanceFieldSymbol::GetSize Method</span><span class="sxs-lookup"><span data-stu-id="5b308-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="5b308-103">Pobiera rozmiar w bajtach pole wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5b308-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b308-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b308-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b308-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b308-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="5b308-106">[out] Wskaźnik do długość pola.</span><span class="sxs-lookup"><span data-stu-id="5b308-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b308-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b308-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b308-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5b308-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b308-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b308-109">Requirements</span></span>  
 <span data-ttu-id="5b308-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b308-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b308-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b308-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b308-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b308-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b308-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b308-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b308-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b308-114">See also</span></span>

- [<span data-ttu-id="5b308-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="5b308-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="5b308-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5b308-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
