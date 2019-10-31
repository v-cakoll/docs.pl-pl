---
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords, Metoda'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6faf8960c06488c8fff5a076aae375529e1d0260
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138878"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="25375-102">ICorDebugSymbolProvider:: GetMergedAssemblyRecords, Metoda</span><span class="sxs-lookup"><span data-stu-id="25375-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="25375-103">Pobiera rekordy symboli dla wszystkich scalonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="25375-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25375-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25375-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25375-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25375-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="25375-106">podczas Liczba żądanych rekordów symboli.</span><span class="sxs-lookup"><span data-stu-id="25375-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="25375-107">określoną Wskaźnik do liczby rekordów symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="25375-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="25375-108">Wskaźnik do tablicy obiektów [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="25375-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25375-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25375-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25375-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="25375-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25375-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25375-111">Requirements</span></span>  
 <span data-ttu-id="25375-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25375-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25375-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25375-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25375-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="25375-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25375-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25375-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25375-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25375-116">See also</span></span>

- [<span data-ttu-id="25375-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="25375-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="25375-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="25375-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
