---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords Method
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b436bd844f917aab3c653428c7cd38809be870b8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771387"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="6bdcd-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span><span class="sxs-lookup"><span data-stu-id="6bdcd-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="6bdcd-103">Pobiera rekordy symboli dla wszystkich zestawów scalone.</span><span class="sxs-lookup"><span data-stu-id="6bdcd-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bdcd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bdcd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bdcd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bdcd-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="6bdcd-106">[in] Liczba żądanych rekordów symboli.</span><span class="sxs-lookup"><span data-stu-id="6bdcd-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="6bdcd-107">[out] Wskaźnik do liczby rekordów symbol pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="6bdcd-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="6bdcd-108">Wskaźnik do tablicy [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bdcd-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bdcd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bdcd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bdcd-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6bdcd-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bdcd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6bdcd-111">Requirements</span></span>  
 <span data-ttu-id="6bdcd-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bdcd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bdcd-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bdcd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bdcd-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bdcd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bdcd-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bdcd-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bdcd-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bdcd-116">See also</span></span>

- [<span data-ttu-id="6bdcd-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="6bdcd-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="6bdcd-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6bdcd-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
