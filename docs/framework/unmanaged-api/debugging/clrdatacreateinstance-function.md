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
ms.openlocfilehash: 73a4a8a2fc737bbf4b49ca859f0549ca7efd54a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701284"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="278d9-102">CLRDataCreateInstance — Funkcja</span><span class="sxs-lookup"><span data-stu-id="278d9-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="278d9-103">Tworzy obiekt interfejs dla elementu określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="278d9-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="278d9-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="278d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="278d9-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="278d9-106">[in] Identyfikator interfejs, który ma zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="278d9-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="278d9-107">[in] Wskaźnik do użytkownika zaimplementowane [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) obiekt, który reprezentuje element docelowy, dla której chcesz utworzyć obiekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="278d9-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="278d9-108">[out] Wskaźnik na adres obiektu zwróconego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="278d9-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="278d9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="278d9-109">Remarks</span></span>  
 <span data-ttu-id="278d9-110">`ICLRDataTarget` Obiektu jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="278d9-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="278d9-111">Implementacja zależy od typu elementu docelowego, reprezentowanego.</span><span class="sxs-lookup"><span data-stu-id="278d9-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="278d9-112">Element docelowy może być procesem, zrzut pamięci, komputer zdalny i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="278d9-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="278d9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="278d9-113">Requirements</span></span>  
 <span data-ttu-id="278d9-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="278d9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="278d9-115">**Nagłówek:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="278d9-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="278d9-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="278d9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="278d9-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="278d9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="278d9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="278d9-118">See also</span></span>

- [<span data-ttu-id="278d9-119">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="278d9-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
