---
title: "IMethodMalloc::Alloc — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae0fa84c08cb8e366db36b6727a3058f24789801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="4f003-102">IMethodMalloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f003-102">IMethodMalloc::Alloc Method</span></span>
<span data-ttu-id="4f003-103">Próbuje przydzielić określonej ilości pamięci dla nowego treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4f003-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f003-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f003-104">Syntax</span></span>  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f003-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f003-105">Parameters</span></span>  
 `cb`  
 <span data-ttu-id="4f003-106">[in] Liczba bajtów do przydzielenia dla treści metody.</span><span class="sxs-lookup"><span data-stu-id="4f003-106">[in] The number of bytes to allocate for the method body.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f003-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f003-107">Remarks</span></span>  
 <span data-ttu-id="4f003-108">Pod adresem większy niż adres bazowy moduł, który jest skojarzony z tym alokatora rozpocznie się alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="4f003-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="4f003-109">Innymi słowy każdego programu przydzielania jest tworzony dla danego modułu i podejmie próbę przydzielenia pamięci z przesunięciem dodatnią z jego adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="4f003-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="4f003-110">Jeśli `Alloc` nie może przydzielić żądanej liczby bajtów pod adresem większy niż adres bazowy moduł, zwraca E_OUTOFMEMORY, niezależnie od rzeczywistej ilości miejsca w pamięci.</span><span class="sxs-lookup"><span data-stu-id="4f003-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>  
  
 <span data-ttu-id="4f003-111">`Alloc` Metody powinny być używane w połączeniu z [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4f003-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f003-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f003-112">Requirements</span></span>  
 <span data-ttu-id="4f003-113">**Platformy:** WindSee [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f003-113">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f003-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f003-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f003-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f003-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f003-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f003-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f003-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f003-117">See Also</span></span>  
 [<span data-ttu-id="4f003-118">IMethodMalloc — interfejs</span><span class="sxs-lookup"><span data-stu-id="4f003-118">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
