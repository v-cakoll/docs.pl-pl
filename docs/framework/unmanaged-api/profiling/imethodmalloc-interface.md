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
ms.openlocfilehash: e9cbf4551c2f8b183e9e6c37a74b13aff3a19ec1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860972"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="31b44-102">IMethodMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="31b44-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="31b44-103">Udostępnia metodę przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="31b44-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31b44-104">Interfejs `IMethodMalloc` jest prostym alokatorem pamięci.</span><span class="sxs-lookup"><span data-stu-id="31b44-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="31b44-105">Umożliwia przydzielanie pamięci, ale nie zwalnia.</span><span class="sxs-lookup"><span data-stu-id="31b44-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31b44-106">Metody</span><span class="sxs-lookup"><span data-stu-id="31b44-106">Methods</span></span>  
  
|<span data-ttu-id="31b44-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="31b44-107">Method</span></span>|<span data-ttu-id="31b44-108">Opis</span><span class="sxs-lookup"><span data-stu-id="31b44-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31b44-109">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="31b44-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="31b44-110">Próbuje przydzielić określoną ilość pamięci dla nowej treści funkcji MSIL.</span><span class="sxs-lookup"><span data-stu-id="31b44-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31b44-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31b44-111">Remarks</span></span>  
 <span data-ttu-id="31b44-112">Każdy Alokator jest specyficzny dla modułu i gwarantuje, że treść funkcji będzie naliczona pozytywnie od podstawy modułu.</span><span class="sxs-lookup"><span data-stu-id="31b44-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="31b44-113">Pamięć powyżej podstawy modułu może być cenna, więc Alokator powinien być używany do przydzielania pamięci tylko dla treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="31b44-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31b44-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31b44-114">Requirements</span></span>  
 <span data-ttu-id="31b44-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31b44-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31b44-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="31b44-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31b44-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="31b44-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31b44-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31b44-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b44-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31b44-119">See also</span></span>

- [<span data-ttu-id="31b44-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="31b44-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
