---
title: "IManagedObject::GetObjectIdentity — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5654865c557e6e004685f66753366d7cb575919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="08924-102">IManagedObject::GetObjectIdentity — Metoda</span><span class="sxs-lookup"><span data-stu-id="08924-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="08924-103">Pobiera tożsamość tego zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="08924-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08924-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08924-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08924-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08924-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="08924-106">[out] Wskaźnik do identyfikatora GUID procesu, w której znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="08924-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="08924-107">[out] Wskaźnik do identyfikator domeny aplikacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="08924-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="08924-108">[out] Wskaźnik do obiektu indeksu w klasycznym modelu COM v-table.</span><span class="sxs-lookup"><span data-stu-id="08924-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08924-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08924-109">Remarks</span></span>  
 <span data-ttu-id="08924-110">Tożsamość obiektu zarządzanego obejmuje proces identyfikator GUID, identyfikator domeny aplikacji i indeks obiektu w klasycznym modelu COM v-table.</span><span class="sxs-lookup"><span data-stu-id="08924-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08924-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08924-111">Requirements</span></span>  
 <span data-ttu-id="08924-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08924-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08924-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08924-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08924-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08924-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08924-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08924-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08924-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08924-116">See Also</span></span>  
 [<span data-ttu-id="08924-117">IManagedObject, interfejs</span><span class="sxs-lookup"><span data-stu-id="08924-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
