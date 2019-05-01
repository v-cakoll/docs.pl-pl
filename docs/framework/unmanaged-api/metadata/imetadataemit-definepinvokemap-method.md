---
title: IMetaDataEmit::DefinePinvokeMap — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15fd75ae807ee5cd7f94f6e650639c3be0628429
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043904"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="ecc8d-102">IMetaDataEmit::DefinePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecc8d-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="ecc8d-103">Ustawia funkcji PInvoke podpis metody odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="ecc8d-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecc8d-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecc8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecc8d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ecc8d-106">[in] Token metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="ecc8d-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="ecc8d-107">[in] Flagi używane przez PInvoke do na potrzeby mapowania.</span><span class="sxs-lookup"><span data-stu-id="ecc8d-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="ecc8d-108">[in] Nazwa elementu docelowego eksportu metody w niezarządzaną biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="ecc8d-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="ecc8d-109">[in] Token dla celu natywnej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="ecc8d-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc8d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecc8d-110">Requirements</span></span>  
 <span data-ttu-id="ecc8d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc8d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc8d-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ecc8d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecc8d-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecc8d-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecc8d-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc8d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc8d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecc8d-115">See also</span></span>

- [<span data-ttu-id="ecc8d-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="ecc8d-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ecc8d-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ecc8d-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
