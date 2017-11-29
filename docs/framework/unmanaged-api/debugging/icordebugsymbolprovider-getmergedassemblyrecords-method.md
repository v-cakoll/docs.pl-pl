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
ms.openlocfilehash: 1f7515479ae5fbe490496bac79f102b02700dcee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="4d0d1-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords — metoda</span><span class="sxs-lookup"><span data-stu-id="4d0d1-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="4d0d1-103">Pobiera rekordy symboli scalone zestawy.</span><span class="sxs-lookup"><span data-stu-id="4d0d1-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d0d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d0d1-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d0d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d0d1-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="4d0d1-106">[in] Liczba żądanych rekordów symbolu.</span><span class="sxs-lookup"><span data-stu-id="4d0d1-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="4d0d1-107">[out] Wskaźnik do liczby rekordów symbol pobieranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="4d0d1-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="4d0d1-108">Wskaźnik do tablicy [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="4d0d1-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d0d1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d0d1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d0d1-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4d0d1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d0d1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d0d1-111">Requirements</span></span>  
 <span data-ttu-id="4d0d1-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d0d1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d0d1-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d0d1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d0d1-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d0d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d0d1-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d0d1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d0d1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d0d1-116">See Also</span></span>  
 [<span data-ttu-id="4d0d1-117">Interfejs ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="4d0d1-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="4d0d1-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="4d0d1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
