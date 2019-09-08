---
title: IAssemblyName::GetDisplayName — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f48f2d95829d2c8111065e5f4ede4e43a16d63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796651"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="a30ea-102">IAssemblyName::GetDisplayName — Metoda</span><span class="sxs-lookup"><span data-stu-id="a30ea-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="a30ea-103">Pobiera nazwę zestawu, do którego odwołuje się ten obiekt [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a30ea-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a30ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a30ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a30ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a30ea-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="a30ea-106">określoną Bufor ciągu, który zawiera nazwę przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a30ea-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="a30ea-107">[in. out] Rozmiar znaków dwubajtowych, `szDisplayName` w tym znak końcowy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="a30ea-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="a30ea-108">podczas Bitowa kombinacja wartości [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) , które mają wpływ na funkcje programu `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="a30ea-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a30ea-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a30ea-109">Requirements</span></span>  
 <span data-ttu-id="a30ea-110">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a30ea-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a30ea-111">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a30ea-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a30ea-112">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a30ea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30ea-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a30ea-113">See also</span></span>

- [<span data-ttu-id="a30ea-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="a30ea-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="a30ea-115">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="a30ea-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
