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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b838a83a160707e546b05ef334eb17d0c6e6cc27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050002"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="6c351-102">IMetaDataEmit::SetPinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c351-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="6c351-103">Ustawia lub zmienia funkcji PInvoke sygnatury metody, zgodnie z wcześniejszym wywołaniu [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="6c351-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c351-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c351-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c351-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c351-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6c351-106">[in] `mdToken` Do mapowania, które informacje mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="6c351-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="6c351-107">[in] Flagi używane przez PInvoke do na potrzeby mapowania.</span><span class="sxs-lookup"><span data-stu-id="6c351-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="6c351-108">Jest to z `CorPinvokeMap` wartości.</span><span class="sxs-lookup"><span data-stu-id="6c351-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="6c351-109">[in] Nazwa elementu docelowego eksportu w natywnej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="6c351-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="6c351-110">[in] `mdModuleRef` Tokenu dla obiektu docelowego niezarządzanych bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="6c351-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c351-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c351-111">Requirements</span></span>  
 <span data-ttu-id="6c351-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c351-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c351-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6c351-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c351-114">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c351-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c351-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c351-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c351-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c351-116">See also</span></span>

- [<span data-ttu-id="6c351-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c351-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6c351-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c351-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
