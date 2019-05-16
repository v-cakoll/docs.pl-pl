---
title: IMethodMalloc::Alloc — Metoda
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66bd56a332dc34fd35f3129256cc0e3d6c5d4508
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636702"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="c2a4d-102">IMethodMalloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2a4d-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="c2a4d-103">Próbuje przydzielić określonej ilości pamięci dla nowej treści funkcji Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="c2a4d-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2a4d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2a4d-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="c2a4d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2a4d-105">Parameters</span></span>

`cb`\
<span data-ttu-id="c2a4d-106">[in] Liczba bajtów do przydzielenia dla treści metody.</span><span class="sxs-lookup"><span data-stu-id="c2a4d-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2a4d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2a4d-107">Remarks</span></span>

 <span data-ttu-id="c2a4d-108">Ilość przydzielonej pamięci rozpocznie się pod adresem większy niż adres podstawowy moduł, który jest skojarzony z tym alokatora.</span><span class="sxs-lookup"><span data-stu-id="c2a4d-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="c2a4d-109">Innymi słowy każdy alokatora jest tworzona dla danego modułu i podejmie próbę przydzielenia pamięci na dodatnią przesunięcie z adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="c2a4d-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="c2a4d-110">Jeśli `Alloc` nie może przydzielić żądanej liczby bajtów pod adresem większy niż adres podstawowy moduł, zwraca E_OUTOFMEMORY niezależnie od rzeczywistej ilości miejsca w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c2a4d-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="c2a4d-111">`Alloc` Metoda powinna służyć w połączeniu z [icorprofilerinfo::setilfunctionbody —](icorprofilerinfo-setilfunctionbody-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c2a4d-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2a4d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2a4d-112">Requirements</span></span>
 <span data-ttu-id="c2a4d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2a4d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="c2a4d-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2a4d-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="c2a4d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2a4d-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="c2a4d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2a4d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c2a4d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2a4d-117">See also</span></span>

- [<span data-ttu-id="c2a4d-118">IMethodMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2a4d-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
