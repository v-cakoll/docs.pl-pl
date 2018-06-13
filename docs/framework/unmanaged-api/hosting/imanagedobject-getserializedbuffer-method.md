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
ms.openlocfilehash: 53e8180fb55336eb05d0737110fd2fe07a4c5894
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441604"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="cf17d-102">IManagedObject::GetSerializedBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf17d-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="cf17d-103">Pobiera reprezentację ciągu tego zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf17d-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf17d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf17d-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf17d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf17d-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="cf17d-106">[out] Wskaźnik do ciąg, który jest Zserializowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="cf17d-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf17d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf17d-107">Remarks</span></span>  
 <span data-ttu-id="cf17d-108">`GetSerializedBuffer` Metody serializuje obiekt, więc mogą być przekazywane do klienta.</span><span class="sxs-lookup"><span data-stu-id="cf17d-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf17d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf17d-109">Requirements</span></span>  
 <span data-ttu-id="cf17d-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf17d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf17d-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf17d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf17d-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf17d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf17d-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf17d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf17d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf17d-114">See Also</span></span>  
 [<span data-ttu-id="cf17d-115">IManagedObject, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf17d-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
