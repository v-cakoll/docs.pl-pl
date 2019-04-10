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
ms.openlocfilehash: 323c883b4010f3ddd4c575e5d5fc40a3419e57c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214367"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="0d962-102">IAssemblyName::GetDisplayName — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d962-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="0d962-103">Pobiera nazwę zrozumiałą dla użytkownika, zestawu odwołuje się ten [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="0d962-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d962-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d962-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d962-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d962-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="0d962-106">[out] Buforu ciągu, który zawiera nazwę przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0d962-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="0d962-107">[out w] Rozmiar `szDisplayName` znaków dwubajtowych, w tym znak terminator o wartości null.</span><span class="sxs-lookup"><span data-stu-id="0d962-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="0d962-108">[in] Bitowa kombinacja [asm_display_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) wartości, które wpływają na funkcje `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="0d962-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d962-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d962-109">Requirements</span></span>  
 <span data-ttu-id="0d962-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d962-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d962-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0d962-111">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="0d962-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0d962-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d962-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d962-113">See also</span></span>

- [<span data-ttu-id="0d962-114">IAssemblyName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0d962-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="0d962-115">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="0d962-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
