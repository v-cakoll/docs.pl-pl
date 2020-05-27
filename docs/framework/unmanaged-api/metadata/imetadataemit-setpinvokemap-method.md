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
ms.openlocfilehash: 0d34c7a2992a2779b96ec87f1a0175d8fcbce34a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007796"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="bac77-102">IMetaDataEmit::SetPinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="bac77-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="bac77-103">Ustawia lub zmienia funkcje podpisu PInvoke metody, zgodnie z definicją w poprzednim wywołaniu [IMetaDataEmit::D efinepinvokemap](imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="bac77-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bac77-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bac77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bac77-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bac77-106">podczas , `mdToken` Do którego mają zastosowanie informacje dotyczące mapowania.</span><span class="sxs-lookup"><span data-stu-id="bac77-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="bac77-107">podczas Flagi używane przez funkcję PInvoke do wykonania mapowania.</span><span class="sxs-lookup"><span data-stu-id="bac77-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="bac77-108">To jest maska bitów `CorPinvokeMap` wartości.</span><span class="sxs-lookup"><span data-stu-id="bac77-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="bac77-109">podczas Nazwa docelowego eksportu w natywnej bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="bac77-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="bac77-110">podczas `mdModuleRef`Token dla docelowej niezarządzanej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="bac77-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac77-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bac77-111">Requirements</span></span>  
 <span data-ttu-id="bac77-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac77-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac77-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bac77-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bac77-114">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bac77-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bac77-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac77-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac77-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bac77-116">See also</span></span>

- [<span data-ttu-id="bac77-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bac77-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="bac77-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bac77-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
