---
title: IAssemblyName::GetName — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c918de10f86442b10b0d85e6554bb1af0a8928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429614"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="f9863-102">IAssemblyName::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9863-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="f9863-103">Pobiera nazwę proste, niezaszyfrowanym zestawu odwołuje się ten [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="f9863-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9863-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9863-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9863-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9863-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="f9863-106">[w, out] Rozmiar `pwzName` znaki dwubajtowe, w tym znak ogranicznika wartości null.</span><span class="sxs-lookup"><span data-stu-id="f9863-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="f9863-107">[out] Bufor aby pomieścić nazwę przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f9863-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9863-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9863-108">Requirements</span></span>  
 <span data-ttu-id="f9863-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9863-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9863-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f9863-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f9863-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9863-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9863-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9863-112">See Also</span></span>  
 [<span data-ttu-id="f9863-113">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f9863-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
