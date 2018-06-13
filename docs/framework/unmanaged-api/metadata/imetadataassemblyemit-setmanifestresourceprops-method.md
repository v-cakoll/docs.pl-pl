---
title: IMetaDataAssemblyEmit::SetManifestResourceProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 755c64aa00b82bf2d8213217787f4dc1916c0898
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443303"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="b3295-102">IMetaDataAssemblyEmit::SetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3295-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="b3295-103">Modyfikuje określony `ManifestResource` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="b3295-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3295-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3295-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3295-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3295-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="b3295-106">[in] Token, który określa `ManifestResource` struktura metadanych ma być zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="b3295-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="b3295-107">[in] Token typu `File` lub `AssemblyRef`, która jest mapowana do dostawcy zasobów.</span><span class="sxs-lookup"><span data-stu-id="b3295-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="b3295-108">[in] Przesunięcie początku zasobów w pliku.</span><span class="sxs-lookup"><span data-stu-id="b3295-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="b3295-109">[in] Bitowe połączenie wartości flagi, które określają atrybuty zasobu.</span><span class="sxs-lookup"><span data-stu-id="b3295-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3295-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3295-110">Remarks</span></span>  
 <span data-ttu-id="b3295-111">Aby utworzyć `ManifestResource` metadanych struktury, użyj [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b3295-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3295-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3295-112">Requirements</span></span>  
 <span data-ttu-id="b3295-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3295-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3295-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3295-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3295-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3295-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3295-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3295-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3295-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3295-117">See Also</span></span>  
 [<span data-ttu-id="b3295-118">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3295-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
