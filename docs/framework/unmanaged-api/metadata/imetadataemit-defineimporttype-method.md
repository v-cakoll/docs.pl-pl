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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177679"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="4b258-102">IMetaDataEmit::DefineImportType — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b258-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="4b258-103">Tworzy odwołanie do określonego typu, który jest zdefiniowany poza bieżącym zakresem i definiuje token dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="4b258-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b258-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b258-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="4b258-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b258-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="4b258-106">[w] [Interfejs IMetaDataAssemblyImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) który reprezentuje zestaw, z którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="4b258-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4b258-107">[w] Tablica zawierająca skrót dla zestawu `pAssemImport`określonego przez program .</span><span class="sxs-lookup"><span data-stu-id="4b258-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4b258-108">[w] Liczba bajtów w `pbHashValue` tablicy.</span><span class="sxs-lookup"><span data-stu-id="4b258-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="4b258-109">[w] Interfejs [IMetaDataImport reprezentujący](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) zakres metadanych, z którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="4b258-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="4b258-110">[w] Token, `mdTypeDef` który określa typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="4b258-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="4b258-111">[w] [Interfejs IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) reprezentujący zestaw, do którego importowany jest typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="4b258-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="4b258-112">[na zewnątrz] Token, `mdTypeRef` który jest zdefiniowany w bieżącym zakresie odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="4b258-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b258-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b258-113">Remarks</span></span>  
 <span data-ttu-id="4b258-114">Przed [wywołaniem metody IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) można użyć `DefineImportType` tej metody, aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej elementu członkowskiego lub interfejsu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4b258-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b258-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b258-115">Requirements</span></span>  
 <span data-ttu-id="4b258-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b258-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b258-117">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b258-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b258-118">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b258-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b258-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b258-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b258-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b258-120">See also</span></span>

- [<span data-ttu-id="4b258-121">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4b258-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4b258-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b258-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
