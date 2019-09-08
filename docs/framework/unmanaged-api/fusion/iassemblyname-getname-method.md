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
ms.openlocfilehash: e471ee99af57ef980850c0a5d3e4f5f2973967ac
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796608"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="98da4-102">IAssemblyName::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="98da4-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="98da4-103">Pobiera prostą, niezaszyfrowaną nazwę zestawu, do którego odwołuje się ten obiekt [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="98da4-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98da4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="98da4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98da4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98da4-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="98da4-106">[in. out] Rozmiar znaków dwubajtowych, `pwzName` w tym znak końcowy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="98da4-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="98da4-107">określoną Bufor przechowujący nazwę przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="98da4-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98da4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98da4-108">Requirements</span></span>  
 <span data-ttu-id="98da4-109">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98da4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98da4-110">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="98da4-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="98da4-111">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98da4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98da4-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98da4-112">See also</span></span>

- [<span data-ttu-id="98da4-113">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="98da4-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
