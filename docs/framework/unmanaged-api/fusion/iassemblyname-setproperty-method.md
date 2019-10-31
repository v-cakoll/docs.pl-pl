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
ms.openlocfilehash: ffa1fa2f5e141728a56f1b598a1aae9602b2ac86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108217"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="e8f55-102">IAssemblyName::SetProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8f55-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="e8f55-103">Ustawia wartość właściwości, do której odwołuje się określony identyfikator właściwości.</span><span class="sxs-lookup"><span data-stu-id="e8f55-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8f55-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8f55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8f55-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="e8f55-106">podczas Unikatowy identyfikator właściwości, której wartość zostanie ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e8f55-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="e8f55-107">podczas Wartość, dla której ma zostać ustawiona właściwość, do której odwołuje się `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="e8f55-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="e8f55-108">podczas Rozmiar w bajtach `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="e8f55-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8f55-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8f55-109">Requirements</span></span>  
 <span data-ttu-id="e8f55-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8f55-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f55-111">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e8f55-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e8f55-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f55-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f55-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8f55-113">See also</span></span>

- [<span data-ttu-id="e8f55-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8f55-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
