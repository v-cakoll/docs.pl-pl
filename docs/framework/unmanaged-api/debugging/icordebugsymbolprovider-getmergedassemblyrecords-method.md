---
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords, Metoda'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f7859b095d80edb5592af1386457ad72b85bc48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957388"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="ae698-102">ICorDebugSymbolProvider:: GetMergedAssemblyRecords, Metoda</span><span class="sxs-lookup"><span data-stu-id="ae698-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="ae698-103">Pobiera rekordy symboli dla wszystkich scalonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="ae698-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae698-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae698-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae698-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae698-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="ae698-106">podczas Liczba żądanych rekordów symboli.</span><span class="sxs-lookup"><span data-stu-id="ae698-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="ae698-107">określoną Wskaźnik do liczby rekordów symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="ae698-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="ae698-108">Wskaźnik do tablicy obiektów [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ae698-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae698-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae698-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae698-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ae698-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae698-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae698-111">Requirements</span></span>  
 <span data-ttu-id="ae698-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae698-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae698-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae698-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae698-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae698-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae698-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae698-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae698-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae698-116">See also</span></span>

- [<span data-ttu-id="ae698-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="ae698-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ae698-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ae698-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
