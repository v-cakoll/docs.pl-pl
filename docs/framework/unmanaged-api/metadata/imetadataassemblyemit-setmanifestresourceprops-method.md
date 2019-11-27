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
ms.openlocfilehash: f6b5e12df60663b75e10b04eaa008a75d720d753
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434432"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="0bddf-102">IMetaDataAssemblyEmit::SetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="0bddf-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="0bddf-103">Modyfikuje określoną strukturę metadanych `ManifestResource`.</span><span class="sxs-lookup"><span data-stu-id="0bddf-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bddf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bddf-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bddf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bddf-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="0bddf-106">podczas Token określający strukturę metadanych `ManifestResource`, która ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="0bddf-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="0bddf-107">podczas Token, typu `File` lub `AssemblyRef`, który jest mapowany do dostawcy zasobów.</span><span class="sxs-lookup"><span data-stu-id="0bddf-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="0bddf-108">podczas Przesunięcie do początku zasobu w pliku.</span><span class="sxs-lookup"><span data-stu-id="0bddf-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="0bddf-109">podczas Bitowa kombinacja wartości flag, które określają atrybuty zasobu.</span><span class="sxs-lookup"><span data-stu-id="0bddf-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bddf-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bddf-110">Remarks</span></span>  
 <span data-ttu-id="0bddf-111">Aby utworzyć `ManifestResource` strukturę metadanych, użyj metody [IMetaDataAssemblyEmit::D efinemanifestresource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0bddf-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bddf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0bddf-112">Requirements</span></span>  
 <span data-ttu-id="0bddf-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bddf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bddf-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0bddf-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0bddf-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0bddf-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0bddf-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bddf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bddf-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bddf-117">See also</span></span>

- [<span data-ttu-id="0bddf-118">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="0bddf-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
