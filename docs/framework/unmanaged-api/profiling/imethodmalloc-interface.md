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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969816"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="a0e5c-102">IMethodMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a0e5c-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="a0e5c-103">Udostępnia metodę można przydzielić pamięci dla nowej treści funkcji Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="a0e5c-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0e5c-104">`IMethodMalloc` Interfejs jest alokatora pamięci proste.</span><span class="sxs-lookup"><span data-stu-id="a0e5c-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="a0e5c-105">Można przydzielić pamięci, ale nie można go bezpłatnie.</span><span class="sxs-lookup"><span data-stu-id="a0e5c-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0e5c-106">Metody</span><span class="sxs-lookup"><span data-stu-id="a0e5c-106">Methods</span></span>  
  
|<span data-ttu-id="a0e5c-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="a0e5c-107">Method</span></span>|<span data-ttu-id="a0e5c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a0e5c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0e5c-109">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="a0e5c-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="a0e5c-110">Próbuje przydzielić określonej ilości pamięci dla nowej treści funkcji MSIL.</span><span class="sxs-lookup"><span data-stu-id="a0e5c-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0e5c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0e5c-111">Remarks</span></span>  
 <span data-ttu-id="a0e5c-112">Każdy alokatora jest specyficzny dla modułu i gwarantuje, że treści funkcji będzie przesunięciem dodatnią od podstawy modułu.</span><span class="sxs-lookup"><span data-stu-id="a0e5c-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="a0e5c-113">Pamięć od podstawy modułu mogą być cenne, alokator powinien być używany do przydzielania pamięci tylko w przypadku treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="a0e5c-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0e5c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0e5c-114">Requirements</span></span>  
 <span data-ttu-id="a0e5c-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0e5c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e5c-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0e5c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0e5c-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0e5c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0e5c-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e5c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e5c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0e5c-119">See also</span></span>

- [<span data-ttu-id="a0e5c-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a0e5c-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
