---
title: IMetaDataEmit::DefineImportType — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7190d2f9d4b64b6a97280914d63c98e505ec70f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649443"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="43322-102">IMetaDataEmit::DefineImportType — Metoda</span><span class="sxs-lookup"><span data-stu-id="43322-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="43322-103">Tworzy odwołanie do określonego typu, który jest zdefiniowane poza bieżącym zakresie i definiuje token dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="43322-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43322-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43322-104">Syntax</span></span>  
  
```  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43322-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43322-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="43322-106">[in] [Imetadataassemblyimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejs, który reprezentuje zestaw, z którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="43322-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="43322-107">[in] Tablica, która zawiera wartość skrótu dla zestawu określonego przez `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="43322-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="43322-108">[in] Liczba bajtów w `pbHashValue` tablicy.</span><span class="sxs-lookup"><span data-stu-id="43322-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="43322-109">[in] [Imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs, który reprezentuje zakres metadanych, z którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="43322-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="43322-110">[in] `mdTypeDef` Token, który określa typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="43322-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="43322-111">[in] [Imetadataassemblyemit —](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interfejs, który reprezentuje zestaw, do którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="43322-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="43322-112">[out] `mdTypeRef` Token, który jest zdefiniowany w bieżącym zakresie dla odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="43322-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43322-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43322-113">Remarks</span></span>  
 <span data-ttu-id="43322-114">Przed wywołaniem [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) metody, można użyć `DefineImportType` metodę, aby utworzyć odwołanie do typu w bieżącym zakresie w klasie nadrzędnej lub interfejs nadrzędny elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="43322-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43322-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43322-115">Requirements</span></span>  
 <span data-ttu-id="43322-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43322-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43322-117">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="43322-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43322-118">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43322-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43322-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43322-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43322-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43322-120">See also</span></span>
- [<span data-ttu-id="43322-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="43322-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="43322-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="43322-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
