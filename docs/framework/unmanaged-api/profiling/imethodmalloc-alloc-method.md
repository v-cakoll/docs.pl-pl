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
ms.openlocfilehash: a82a2150f32b1b335da083ca235ed9d2966a0b6e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494205"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="8ce30-102">IMethodMalloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ce30-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="8ce30-103">Próbuje przydzielić określoną ilość pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8ce30-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="8ce30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ce30-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="8ce30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ce30-105">Parameters</span></span>

`cb`\
<span data-ttu-id="8ce30-106">podczas Liczba bajtów do przydzielenia dla treści metody.</span><span class="sxs-lookup"><span data-stu-id="8ce30-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ce30-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ce30-107">Remarks</span></span>

 <span data-ttu-id="8ce30-108">Przydzieloną pamięć rozpocznie się pod adresem większym niż adres podstawowy modułu, który jest skojarzony z tym alokatorem.</span><span class="sxs-lookup"><span data-stu-id="8ce30-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="8ce30-109">Innymi słowy, każdy Alokator jest tworzony dla danego modułu i podejmie próbę przydzielenia pamięci z przesunięciem pozytywnym od jego adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="8ce30-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="8ce30-110">Jeśli `Alloc` żądana liczba bajtów w adresie większym niż adres bazowy modułu nie powiedzie się, zwraca E_OUTOFMEMORY, niezależnie od rzeczywistej ilości dostępnego miejsca w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8ce30-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="8ce30-111">`Alloc`Metoda powinna być używana w połączeniu z metodą [ICorProfilerInfo:: SetILFunctionBody —](icorprofilerinfo-setilfunctionbody-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8ce30-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8ce30-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ce30-112">Requirements</span></span>
 <span data-ttu-id="8ce30-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ce30-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="8ce30-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8ce30-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="8ce30-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8ce30-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="8ce30-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce30-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8ce30-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ce30-117">See also</span></span>

- [<span data-ttu-id="8ce30-118">IMethodMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ce30-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
