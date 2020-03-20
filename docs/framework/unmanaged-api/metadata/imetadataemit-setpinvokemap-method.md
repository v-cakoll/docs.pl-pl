---
title: IMetaDataEmit::SetPinvokeMap — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 4c68754bc44fe035fd8e7143c52895928beae395
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175593"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="6320e-102">IMetaDataEmit::SetPinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="6320e-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="6320e-103">Ustawia lub zmienia funkcje podpisu PInvoke metody, zgodnie z definicją wcześniejszego wywołania [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="6320e-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6320e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6320e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6320e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6320e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6320e-106">[w] Informacje `mdToken` o mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="6320e-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="6320e-107">[w] Flagi używane przez PInvoke do mapowania.</span><span class="sxs-lookup"><span data-stu-id="6320e-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="6320e-108">Jest to maska `CorPinvokeMap` bitowa wartości.</span><span class="sxs-lookup"><span data-stu-id="6320e-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="6320e-109">[w] Nazwa docelowego eksportu w macierzystej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="6320e-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="6320e-110">[w] Token `mdModuleRef` dla docelowej biblioteki DLL niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="6320e-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6320e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6320e-111">Requirements</span></span>  
 <span data-ttu-id="6320e-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6320e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6320e-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="6320e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6320e-114">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6320e-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6320e-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6320e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6320e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6320e-116">See also</span></span>

- [<span data-ttu-id="6320e-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6320e-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6320e-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6320e-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
