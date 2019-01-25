---
title: PFN_CLRDataCreateInstance — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46e039aeec352c215046bebfb17e6fbd803962a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597492"
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="de3ff-102">PFN_CLRDataCreateInstance — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="de3ff-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="de3ff-103">Wskazuje funkcję, która tworzy obiekt interfejs dla elementu określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="de3ff-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de3ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de3ff-104">Syntax</span></span>  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de3ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de3ff-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="de3ff-106">[in] Identyfikator interfejs, który ma zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="de3ff-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="de3ff-107">[in] Wskaźnik do użytkownika zaimplementowane [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) obiekt, który reprezentuje element docelowy, dla której chcesz utworzyć obiekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="de3ff-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="de3ff-108">[out] Wskaźnik na adres obiektu zwróconego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="de3ff-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de3ff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de3ff-109">Remarks</span></span>  
 <span data-ttu-id="de3ff-110">`ICLRDataTarget` Obiektu jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de3ff-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="de3ff-111">Implementacja zależy od typu elementu docelowego, reprezentowanego.</span><span class="sxs-lookup"><span data-stu-id="de3ff-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="de3ff-112">Element docelowy może być procesem, zrzut pamięci, komputer zdalny i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="de3ff-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de3ff-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de3ff-113">Requirements</span></span>  
 <span data-ttu-id="de3ff-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de3ff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de3ff-115">**Nagłówek:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="de3ff-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="de3ff-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de3ff-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de3ff-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de3ff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3ff-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de3ff-118">See also</span></span>
- [<span data-ttu-id="de3ff-119">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="de3ff-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
