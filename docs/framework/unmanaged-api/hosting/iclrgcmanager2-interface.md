---
title: ICLRGCManager2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: 0f3ecc0d497eaee937647df47ba0956335a2fe41
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703941"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="c0b47-102">ICLRGCManager2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c0b47-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="c0b47-103">Dostarcza metody, które umożliwiają hostowi współdziałanie z systemem odzyskiwania pamięci środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c0b47-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0b47-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c0b47-104">Methods</span></span>  
  
|<span data-ttu-id="c0b47-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c0b47-105">Method</span></span>|<span data-ttu-id="c0b47-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c0b47-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0b47-107">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="c0b47-107">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="c0b47-108">Ustawia rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji 0 systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="c0b47-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="c0b47-109">Włącza wartość generacji 0 i rozmiary segmentów większe niż `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="c0b47-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0b47-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0b47-110">Remarks</span></span>  
 <span data-ttu-id="c0b47-111">Ten interfejs dziedziczy z [interfejsu ICLRGCManager](iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c0b47-111">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="c0b47-112">Środowisko uruchomieniowe języka wspólnego (CLR) implementuje mechanizm wyrzucania elementów bezużytecznych z typem zarządzanym <xref:System.GC> .</span><span class="sxs-lookup"><span data-stu-id="c0b47-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="c0b47-113">Aby uzyskać więcej informacji na temat systemu wyrzucania elementów bezużytecznych, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="c0b47-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0b47-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0b47-114">Requirements</span></span>  
 <span data-ttu-id="c0b47-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0b47-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0b47-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c0b47-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0b47-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c0b47-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0b47-118">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0b47-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b47-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0b47-119">See also</span></span>

- [<span data-ttu-id="c0b47-120">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="c0b47-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="c0b47-121">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="c0b47-121">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="c0b47-122">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c0b47-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c0b47-123">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="c0b47-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="c0b47-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c0b47-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c0b47-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="c0b47-125">Hosting</span></span>](index.md)
