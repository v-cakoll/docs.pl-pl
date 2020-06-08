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
ms.openlocfilehash: 12b97b28383eb7c39f20ee0e88f55d48e60ad956
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494114"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="cd3c2-102">IMethodMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd3c2-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="cd3c2-103">Udostępnia metodę przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cd3c2-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd3c2-104">`IMethodMalloc`Interfejs jest prostym alokatorem pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd3c2-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="cd3c2-105">Umożliwia przydzielanie pamięci, ale nie zwalnia.</span><span class="sxs-lookup"><span data-stu-id="cd3c2-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd3c2-106">Metody</span><span class="sxs-lookup"><span data-stu-id="cd3c2-106">Methods</span></span>  
  
|<span data-ttu-id="cd3c2-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="cd3c2-107">Method</span></span>|<span data-ttu-id="cd3c2-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cd3c2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd3c2-109">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="cd3c2-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="cd3c2-110">Próbuje przydzielić określoną ilość pamięci dla nowej treści funkcji MSIL.</span><span class="sxs-lookup"><span data-stu-id="cd3c2-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd3c2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd3c2-111">Remarks</span></span>  
 <span data-ttu-id="cd3c2-112">Każdy Alokator jest specyficzny dla modułu i gwarantuje, że treść funkcji będzie naliczona pozytywnie od podstawy modułu.</span><span class="sxs-lookup"><span data-stu-id="cd3c2-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="cd3c2-113">Pamięć powyżej podstawy modułu może być cenna, więc Alokator powinien być używany do przydzielania pamięci tylko dla treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="cd3c2-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd3c2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd3c2-114">Requirements</span></span>  
 <span data-ttu-id="cd3c2-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd3c2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd3c2-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cd3c2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd3c2-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cd3c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd3c2-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd3c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3c2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd3c2-119">See also</span></span>

- [<span data-ttu-id="cd3c2-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cd3c2-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
