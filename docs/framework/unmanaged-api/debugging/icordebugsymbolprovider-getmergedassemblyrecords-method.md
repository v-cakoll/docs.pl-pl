---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords Method
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9003482860e554049c39ea9ffed4c52345bfeff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953312"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="92ee3-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span><span class="sxs-lookup"><span data-stu-id="92ee3-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="92ee3-103">Pobiera rekordy symboli dla wszystkich zestawów scalone.</span><span class="sxs-lookup"><span data-stu-id="92ee3-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92ee3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92ee3-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92ee3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92ee3-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="92ee3-106">[in] Liczba żądanych rekordów symboli.</span><span class="sxs-lookup"><span data-stu-id="92ee3-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="92ee3-107">[out] Wskaźnik do liczby rekordów symbol pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="92ee3-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="92ee3-108">Wskaźnik do tablicy [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="92ee3-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92ee3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92ee3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92ee3-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="92ee3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92ee3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92ee3-111">Requirements</span></span>  
 <span data-ttu-id="92ee3-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92ee3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92ee3-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92ee3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92ee3-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92ee3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92ee3-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92ee3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ee3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92ee3-116">See also</span></span>

- [<span data-ttu-id="92ee3-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="92ee3-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="92ee3-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="92ee3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
