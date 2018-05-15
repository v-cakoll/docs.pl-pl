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
ms.openlocfilehash: 00a95646323a5ee08d6758b0f6a7c493c661705d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="846b9-102">IAssemblyName::GetDisplayName — Metoda</span><span class="sxs-lookup"><span data-stu-id="846b9-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="846b9-103">Pobiera nazwę zrozumiałą zestawu odwołuje się ten [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="846b9-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="846b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="846b9-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="846b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="846b9-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="846b9-106">[out] Bufor ciąg zawierający nazwę przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="846b9-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="846b9-107">[w, out] Rozmiar `szDisplayName` znaki dwubajtowe, w tym znaków terminatorem null.</span><span class="sxs-lookup"><span data-stu-id="846b9-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="846b9-108">[in] Bitowe połączenie [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) wartości wpływających na funkcje `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="846b9-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="846b9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="846b9-109">Requirements</span></span>  
 <span data-ttu-id="846b9-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="846b9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="846b9-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="846b9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="846b9-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="846b9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846b9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="846b9-113">See Also</span></span>  
 [<span data-ttu-id="846b9-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="846b9-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="846b9-115">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="846b9-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
