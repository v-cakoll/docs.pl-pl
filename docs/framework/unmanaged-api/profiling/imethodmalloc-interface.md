---
title: IMethodMalloc — Interfejs
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 3f840154d472dbcea7dfef7ba93e38c80b836734
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447549"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="3ae06-102">IMethodMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3ae06-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="3ae06-103">Udostępnia metodę przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3ae06-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ae06-104">Interfejs `IMethodMalloc` jest prostym alokatorem pamięci.</span><span class="sxs-lookup"><span data-stu-id="3ae06-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="3ae06-105">Umożliwia przydzielanie pamięci, ale nie zwalnia.</span><span class="sxs-lookup"><span data-stu-id="3ae06-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ae06-106">Metody</span><span class="sxs-lookup"><span data-stu-id="3ae06-106">Methods</span></span>  
  
|<span data-ttu-id="3ae06-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="3ae06-107">Method</span></span>|<span data-ttu-id="3ae06-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3ae06-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ae06-109">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="3ae06-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="3ae06-110">Próbuje przydzielić określoną ilość pamięci dla nowej treści funkcji MSIL.</span><span class="sxs-lookup"><span data-stu-id="3ae06-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ae06-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ae06-111">Remarks</span></span>  
 <span data-ttu-id="3ae06-112">Każdy Alokator jest specyficzny dla modułu i gwarantuje, że treść funkcji będzie naliczona pozytywnie od podstawy modułu.</span><span class="sxs-lookup"><span data-stu-id="3ae06-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="3ae06-113">Pamięć powyżej podstawy modułu może być cenna, więc Alokator powinien być używany do przydzielania pamięci tylko dla treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="3ae06-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ae06-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ae06-114">Requirements</span></span>  
 <span data-ttu-id="3ae06-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ae06-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ae06-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3ae06-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ae06-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ae06-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ae06-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ae06-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae06-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ae06-119">See also</span></span>

- [<span data-ttu-id="3ae06-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3ae06-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
