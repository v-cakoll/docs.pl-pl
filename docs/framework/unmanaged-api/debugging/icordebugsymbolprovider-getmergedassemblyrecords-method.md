---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords Method
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9003482860e554049c39ea9ffed4c52345bfeff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183212"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="270b6-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span><span class="sxs-lookup"><span data-stu-id="270b6-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="270b6-103">Pobiera rekordy symboli dla wszystkich zestawów scalone.</span><span class="sxs-lookup"><span data-stu-id="270b6-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="270b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="270b6-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="270b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="270b6-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="270b6-106">[in] Liczba żądanych rekordów symboli.</span><span class="sxs-lookup"><span data-stu-id="270b6-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="270b6-107">[out] Wskaźnik do liczby rekordów symbol pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="270b6-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="270b6-108">Wskaźnik do tablicy [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="270b6-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="270b6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="270b6-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="270b6-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="270b6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="270b6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="270b6-111">Requirements</span></span>  
 <span data-ttu-id="270b6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="270b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="270b6-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="270b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="270b6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="270b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="270b6-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="270b6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="270b6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="270b6-116">See also</span></span>

- [<span data-ttu-id="270b6-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="270b6-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="270b6-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="270b6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
