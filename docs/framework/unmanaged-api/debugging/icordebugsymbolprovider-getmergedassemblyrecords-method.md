---
title: "ICorDebugSymbolProvider::GetMergedAssemblyRecords — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75c8a98b4e7b2e3250adfb75a5d2dcb29a71ff27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="36aed-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords — metoda</span><span class="sxs-lookup"><span data-stu-id="36aed-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="36aed-103">Pobiera rekordy symboli scalone zestawy.</span><span class="sxs-lookup"><span data-stu-id="36aed-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36aed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36aed-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36aed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36aed-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="36aed-106">[in] Liczba żądanych rekordów symbolu.</span><span class="sxs-lookup"><span data-stu-id="36aed-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="36aed-107">[out] Wskaźnik do liczby rekordów symbol pobieranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="36aed-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="36aed-108">Wskaźnik do tablicy [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="36aed-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36aed-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36aed-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36aed-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36aed-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36aed-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36aed-111">Requirements</span></span>  
 <span data-ttu-id="36aed-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36aed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36aed-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36aed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36aed-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36aed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36aed-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36aed-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36aed-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36aed-116">See Also</span></span>  
 [<span data-ttu-id="36aed-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="36aed-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="36aed-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="36aed-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
