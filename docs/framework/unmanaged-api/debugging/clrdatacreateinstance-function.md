---
title: CLRDataCreateInstance — Funkcja
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9d4965751db1a70871270317a644b0acb1302f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="24c01-102">CLRDataCreateInstance — Funkcja</span><span class="sxs-lookup"><span data-stu-id="24c01-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="24c01-103">Tworzy obiekt interfejs dla elementu określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="24c01-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24c01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24c01-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24c01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24c01-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="24c01-106">[in] Identyfikator interfejsu, który ma zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="24c01-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="24c01-107">[in] Wskaźnik do użytkownika zaimplementowana [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) obiekt, który reprezentuje element docelowy, dla którego ma zostać utworzony obiekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="24c01-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="24c01-108">[out] Wskaźnik do adresu obiektu zwróconego interface.</span><span class="sxs-lookup"><span data-stu-id="24c01-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24c01-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24c01-109">Remarks</span></span>  
 <span data-ttu-id="24c01-110">`ICLRDataTarget` Obiektu jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24c01-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="24c01-111">Implementacja zależy od typu reprezentowanego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="24c01-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="24c01-112">Element docelowy może być procesu, zrzutu pamięci, komputer zdalny i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="24c01-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24c01-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24c01-113">Requirements</span></span>  
 <span data-ttu-id="24c01-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24c01-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24c01-115">**Nagłówek:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="24c01-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="24c01-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24c01-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24c01-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24c01-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c01-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24c01-118">See Also</span></span>  
 [<span data-ttu-id="24c01-119">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="24c01-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
