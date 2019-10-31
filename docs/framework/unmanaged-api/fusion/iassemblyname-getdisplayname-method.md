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
ms.openlocfilehash: 5dbb5dc483bc5a08c59606654d55b5a62266e509
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134367"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="dabbd-102">IAssemblyName::GetDisplayName — Metoda</span><span class="sxs-lookup"><span data-stu-id="dabbd-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="dabbd-103">Pobiera nazwę zestawu, do którego odwołuje się ten obiekt [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="dabbd-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dabbd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dabbd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dabbd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dabbd-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="dabbd-106">określoną Bufor ciągu, który zawiera nazwę przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="dabbd-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="dabbd-107">[in. out] Rozmiar `szDisplayName` w postaci znaków dwubajtowych, łącznie z znakiem terminatora o wartości null.</span><span class="sxs-lookup"><span data-stu-id="dabbd-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="dabbd-108">podczas Bitowa kombinacja wartości [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) , które mają wpływ na funkcje `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="dabbd-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dabbd-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dabbd-109">Requirements</span></span>  
 <span data-ttu-id="dabbd-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dabbd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dabbd-111">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="dabbd-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="dabbd-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dabbd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dabbd-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dabbd-113">See also</span></span>

- [<span data-ttu-id="dabbd-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="dabbd-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="dabbd-115">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="dabbd-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
