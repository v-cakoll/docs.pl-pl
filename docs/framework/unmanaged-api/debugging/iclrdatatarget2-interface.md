---
title: ICLRDataTarget2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d21bced214242866c47f40f392593f3f51cda02f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697943"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="4ad04-102">ICLRDataTarget2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4ad04-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="4ad04-103">Podklasa klasy [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) używany przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="4ad04-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4ad04-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4ad04-104">Methods</span></span>  
  
|<span data-ttu-id="4ad04-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4ad04-105">Method</span></span>|<span data-ttu-id="4ad04-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4ad04-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ad04-107">AllocVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="4ad04-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="4ad04-108">Przydziela pamięć w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4ad04-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="4ad04-109">FreeVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="4ad04-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="4ad04-110">Zwalnia pamięć, która była przydzielona wcześniej w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4ad04-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ad04-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ad04-111">Remarks</span></span>  
 <span data-ttu-id="4ad04-112">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4ad04-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="4ad04-113">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="4ad04-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="4ad04-114">Cel może nie obsługiwać modyfikacji regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="4ad04-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad04-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ad04-115">Requirements</span></span>  
 <span data-ttu-id="4ad04-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ad04-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ad04-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4ad04-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4ad04-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ad04-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ad04-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ad04-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad04-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ad04-120">See also</span></span>

- [<span data-ttu-id="4ad04-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ad04-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="4ad04-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4ad04-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
