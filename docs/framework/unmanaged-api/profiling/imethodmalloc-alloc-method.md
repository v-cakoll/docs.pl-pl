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
ms.openlocfilehash: 9a676989bdc6866f85fabe3e15b1e6b7b8b5a9a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000717"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="b7bd8-102">IMethodMalloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7bd8-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="b7bd8-103">Próbuje przydzielić określonej ilości pamięci dla nowej treści funkcji Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="b7bd8-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7bd8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7bd8-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="b7bd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7bd8-105">Parameters</span></span>

`cb`\
<span data-ttu-id="b7bd8-106">[in] Liczba bajtów do przydzielenia dla treści metody.</span><span class="sxs-lookup"><span data-stu-id="b7bd8-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7bd8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7bd8-107">Remarks</span></span>

 <span data-ttu-id="b7bd8-108">Ilość przydzielonej pamięci rozpocznie się pod adresem większy niż adres podstawowy moduł, który jest skojarzony z tym alokatora.</span><span class="sxs-lookup"><span data-stu-id="b7bd8-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="b7bd8-109">Innymi słowy każdy alokatora jest tworzona dla danego modułu i podejmie próbę przydzielenia pamięci na dodatnią przesunięcie z adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="b7bd8-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="b7bd8-110">Jeśli `Alloc` nie może przydzielić żądanej liczby bajtów pod adresem większy niż adres podstawowy moduł, zwraca E_OUTOFMEMORY niezależnie od rzeczywistej ilości miejsca w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b7bd8-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="b7bd8-111">`Alloc` Metoda powinna służyć w połączeniu z [icorprofilerinfo::setilfunctionbody —](icorprofilerinfo-setilfunctionbody-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b7bd8-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7bd8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7bd8-112">Requirements</span></span>
 <span data-ttu-id="b7bd8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7bd8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="b7bd8-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7bd8-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="b7bd8-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7bd8-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="b7bd8-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7bd8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b7bd8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7bd8-117">See also</span></span>

- [<span data-ttu-id="b7bd8-118">IMethodMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7bd8-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)