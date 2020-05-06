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
ms.openlocfilehash: 6b2700b2f12e312f06640a06e5ec82fbc58f2ca9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860460"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="1401b-102">ICLRDataTarget2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1401b-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="1401b-103">Podklasa elementu [ICLRDataTarget](iclrdatatarget-interface.md) , która jest używana przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="1401b-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1401b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1401b-104">Methods</span></span>  
  
|<span data-ttu-id="1401b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1401b-105">Method</span></span>|<span data-ttu-id="1401b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1401b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1401b-107">AllocVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="1401b-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="1401b-108">Przydziela pamięć w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="1401b-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="1401b-109">FreeVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="1401b-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="1401b-110">Zwalnia pamięć, która została wcześniej przypisana w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="1401b-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1401b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1401b-111">Remarks</span></span>  
 <span data-ttu-id="1401b-112">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="1401b-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="1401b-113">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="1401b-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="1401b-114">Cel może nie obsługiwać modyfikacji regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="1401b-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1401b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1401b-115">Requirements</span></span>  
 <span data-ttu-id="1401b-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1401b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1401b-117">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="1401b-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1401b-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1401b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1401b-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1401b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1401b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1401b-120">See also</span></span>

- [<span data-ttu-id="1401b-121">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1401b-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="1401b-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1401b-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
