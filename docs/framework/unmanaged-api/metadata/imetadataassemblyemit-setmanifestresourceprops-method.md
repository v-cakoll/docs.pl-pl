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
ms.openlocfilehash: d92129bd7c51ba2fa574f8337ba2b3727ab7b172
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599052"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="02552-102">IMetaDataAssemblyEmit::SetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="02552-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="02552-103">Modyfikuje określonego `ManifestResource` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="02552-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02552-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02552-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02552-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02552-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="02552-106">[in] Token, który określa `ManifestResource` struktury metadanych do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="02552-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="02552-107">[in] Token typu `File` lub `AssemblyRef`, która jest mapowana na potrzeby dostawcy zasobów.</span><span class="sxs-lookup"><span data-stu-id="02552-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="02552-108">[in] Przesunięcie początku zasobu w pliku.</span><span class="sxs-lookup"><span data-stu-id="02552-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="02552-109">[in] Bitowa kombinacja wartości flagi, które określają atrybuty zasobu.</span><span class="sxs-lookup"><span data-stu-id="02552-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02552-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02552-110">Remarks</span></span>  
 <span data-ttu-id="02552-111">Aby utworzyć `ManifestResource` struktury metadanych, użyj [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="02552-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02552-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02552-112">Requirements</span></span>  
 <span data-ttu-id="02552-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02552-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02552-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="02552-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02552-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02552-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02552-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02552-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02552-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02552-117">See also</span></span>
- [<span data-ttu-id="02552-118">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="02552-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
