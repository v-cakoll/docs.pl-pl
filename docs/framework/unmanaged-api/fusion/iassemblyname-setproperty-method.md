---
title: IAssemblyName::SetProperty — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cc2a2c7991eb4d11873ebb6a2df92ccc45cde9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697228"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="1432e-102">IAssemblyName::SetProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="1432e-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="1432e-103">Ustawia wartość właściwości odwołuje się określony identyfikator właściwości.</span><span class="sxs-lookup"><span data-stu-id="1432e-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1432e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1432e-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1432e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1432e-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="1432e-106">[in] Unikatowy identyfikator właściwości, którego wartość zostanie ustawiona.</span><span class="sxs-lookup"><span data-stu-id="1432e-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="1432e-107">[in] Wartość, do którego można ustawić właściwości odwołuje się `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="1432e-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="1432e-108">[in] Rozmiar w bajtach z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="1432e-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1432e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1432e-109">Requirements</span></span>  
 <span data-ttu-id="1432e-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1432e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1432e-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1432e-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1432e-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1432e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1432e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1432e-113">See also</span></span>

- [<span data-ttu-id="1432e-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="1432e-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
