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
ms.openlocfilehash: 9af0773c2ef066c103f823e4d28c0fd6e9eadc24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697384"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="7047c-102">IAssemblyName::GetProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="7047c-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="7047c-103">Pobiera wskaźnik do właściwości odwołuje się określony identyfikator właściwości.</span><span class="sxs-lookup"><span data-stu-id="7047c-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7047c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7047c-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7047c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7047c-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="7047c-106">[in] Unikatowy identyfikator dla żądanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="7047c-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="7047c-107">[out] Dane zwrócone właściwości.</span><span class="sxs-lookup"><span data-stu-id="7047c-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="7047c-108">[out w] Rozmiar w bajtach z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="7047c-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7047c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7047c-109">Requirements</span></span>  
 <span data-ttu-id="7047c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7047c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7047c-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7047c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7047c-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7047c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7047c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7047c-113">See also</span></span>

- [<span data-ttu-id="7047c-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7047c-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
