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
ms.openlocfilehash: 68e6f7599db55ed9429f159b380a8a9f8ae3f034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="4f233-102">IMetaDataEmit::DefineImportType — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f233-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="4f233-103">Tworzy odwołanie do określonego typu, który jest zdefiniowany poza bieżącym zakresem i definiuje token dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="4f233-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f233-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f233-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="4f233-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f233-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="4f233-106">[in] [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejs, który reprezentuje zestaw, z którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="4f233-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4f233-107">[in] Tablica zawierająca wartość skrótu dla zestawu określony przez `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="4f233-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4f233-108">[in] Liczba bajtów w `pbHashValue` tablicy.</span><span class="sxs-lookup"><span data-stu-id="4f233-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="4f233-109">[in] [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs, który reprezentuje zakres metadanych, z którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="4f233-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="4f233-110">[in] `mdTypeDef` Token, który określa typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="4f233-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="4f233-111">[in] [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interfejs, który reprezentuje zestaw, do którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="4f233-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="4f233-112">[out] `mdTypeRef` Token, który jest zdefiniowany w bieżącym zakresie dla odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="4f233-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f233-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f233-113">Remarks</span></span>  
 <span data-ttu-id="4f233-114">Przed wywołaniem [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) metody, można użyć `DefineImportType` metodę, aby utworzyć odwołanie do typu w bieżącym zakresie klasy nadrzędnej lub interfejs nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="4f233-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f233-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f233-115">Requirements</span></span>  
 <span data-ttu-id="4f233-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f233-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f233-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4f233-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f233-118">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f233-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f233-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f233-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f233-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f233-120">See Also</span></span>  
 [<span data-ttu-id="4f233-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f233-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4f233-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f233-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
