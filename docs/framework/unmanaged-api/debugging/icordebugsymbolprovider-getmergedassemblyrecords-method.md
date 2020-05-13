---
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords, Metoda'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: b7d26fa80a7a8ebe7b4606b914c8cd09c52df1e4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379624"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="f4554-102">ICorDebugSymbolProvider:: GetMergedAssemblyRecords, Metoda</span><span class="sxs-lookup"><span data-stu-id="f4554-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="f4554-103">Pobiera rekordy symboli dla wszystkich scalonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="f4554-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4554-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4554-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4554-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4554-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="f4554-106">podczas Liczba żądanych rekordów symboli.</span><span class="sxs-lookup"><span data-stu-id="f4554-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="f4554-107">określoną Wskaźnik do liczby rekordów symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f4554-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="f4554-108">Wskaźnik do tablicy obiektów [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f4554-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4554-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4554-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4554-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f4554-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4554-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4554-111">Requirements</span></span>  
 <span data-ttu-id="f4554-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4554-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4554-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f4554-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4554-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f4554-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4554-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4554-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4554-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4554-116">See also</span></span>

- [<span data-ttu-id="f4554-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4554-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f4554-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f4554-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
