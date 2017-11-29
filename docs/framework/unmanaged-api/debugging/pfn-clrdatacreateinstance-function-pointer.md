---
title: "PFN_CLRDataCreateInstance — Wskaźnik funkcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PFN_CLRDataCreateInstance
api_location: mscordbi.dll
api_type: COM
f1_keywords: PFN_CLRDataCreateInstance
helpviewer_keywords: PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7ec5783381c667d666c447b6d9861d9baaad3907
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="9a4e7-102">PFN_CLRDataCreateInstance — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="9a4e7-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="9a4e7-103">Punkty do funkcji, która tworzy obiekt interfejs dla elementu określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9a4e7-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a4e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a4e7-104">Syntax</span></span>  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a4e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a4e7-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="9a4e7-106">[in] Identyfikator interfejsu, który ma zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="9a4e7-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="9a4e7-107">[in] Wskaźnik do użytkownika zaimplementowana [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) obiekt, który reprezentuje element docelowy, dla którego ma zostać utworzony obiekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9a4e7-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="9a4e7-108">[out] Wskaźnik do adresu obiektu zwróconego interface.</span><span class="sxs-lookup"><span data-stu-id="9a4e7-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a4e7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a4e7-109">Remarks</span></span>  
 <span data-ttu-id="9a4e7-110">`ICLRDataTarget` Obiektu jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a4e7-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="9a4e7-111">Implementacja zależy od typu reprezentowanego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9a4e7-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="9a4e7-112">Element docelowy może być procesu, zrzutu pamięci, komputer zdalny i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9a4e7-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a4e7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a4e7-113">Requirements</span></span>  
 <span data-ttu-id="9a4e7-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a4e7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a4e7-115">**Nagłówek:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="9a4e7-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="9a4e7-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a4e7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a4e7-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a4e7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a4e7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a4e7-118">See Also</span></span>  
 [<span data-ttu-id="9a4e7-119">Statyczne funkcje globalne debugowania</span><span class="sxs-lookup"><span data-stu-id="9a4e7-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
