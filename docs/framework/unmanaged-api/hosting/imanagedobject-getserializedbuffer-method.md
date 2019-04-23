---
title: IManagedObject::GetSerializedBuffer — Metoda
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb9242160b684b3c7b90756d7b20811ad162fc30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156146"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="b0c08-102">IManagedObject::GetSerializedBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0c08-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="b0c08-103">Pobiera reprezentację ciągu tego zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b0c08-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0c08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0c08-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0c08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0c08-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="b0c08-106">[out] Wskaźnik do ciągu, który jest Zserializowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="b0c08-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0c08-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0c08-107">Remarks</span></span>  
 <span data-ttu-id="b0c08-108">`GetSerializedBuffer` Metoda serializuje obiekt, dzięki czemu mogą być przekazywane do klienta.</span><span class="sxs-lookup"><span data-stu-id="b0c08-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0c08-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0c08-109">Requirements</span></span>  
 <span data-ttu-id="b0c08-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0c08-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0c08-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b0c08-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0c08-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0c08-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0c08-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0c08-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c08-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0c08-114">See also</span></span>

- [<span data-ttu-id="b0c08-115">IManagedObject, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0c08-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
