---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords — metoda
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 502e7e0b52bb147b5fe37dcc6e4f6d13d642b6f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417547"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="b93d2-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords — metoda</span><span class="sxs-lookup"><span data-stu-id="b93d2-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="b93d2-103">Pobiera rekordy symboli scalone zestawy.</span><span class="sxs-lookup"><span data-stu-id="b93d2-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b93d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b93d2-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b93d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b93d2-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="b93d2-106">[in] Liczba żądanych rekordów symbolu.</span><span class="sxs-lookup"><span data-stu-id="b93d2-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="b93d2-107">[out] Wskaźnik do liczby rekordów symbol pobieranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="b93d2-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="b93d2-108">Wskaźnik do tablicy [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="b93d2-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b93d2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b93d2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b93d2-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b93d2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b93d2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b93d2-111">Requirements</span></span>  
 <span data-ttu-id="b93d2-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b93d2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b93d2-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b93d2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b93d2-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b93d2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b93d2-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b93d2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b93d2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b93d2-116">See Also</span></span>  
 [<span data-ttu-id="b93d2-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="b93d2-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="b93d2-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b93d2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
