---
title: IAssemblyName::GetProperty — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 351d540d226f46f180b46323e83eb1bcc71da4f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796589"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="35b4f-102">IAssemblyName::GetProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="35b4f-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="35b4f-103">Pobiera wskaźnik do właściwości, do której odwołuje się określony identyfikator właściwości.</span><span class="sxs-lookup"><span data-stu-id="35b4f-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35b4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35b4f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35b4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35b4f-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="35b4f-106">podczas Unikatowy identyfikator dla żądanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="35b4f-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="35b4f-107">określoną Zwrócone dane właściwości.</span><span class="sxs-lookup"><span data-stu-id="35b4f-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="35b4f-108">[in. out] Rozmiar, w bajtach, z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="35b4f-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35b4f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35b4f-109">Requirements</span></span>  
 <span data-ttu-id="35b4f-110">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35b4f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35b4f-111">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="35b4f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="35b4f-112">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35b4f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b4f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35b4f-113">See also</span></span>

- [<span data-ttu-id="35b4f-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="35b4f-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
