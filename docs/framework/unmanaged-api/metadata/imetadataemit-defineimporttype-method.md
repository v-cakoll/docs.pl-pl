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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004698"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="f9cd7-102">IMetaDataEmit::DefineImportType — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9cd7-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="f9cd7-103">Tworzy odwołanie do określonego typu, który jest zdefiniowany poza bieżącym zakresem, i definiuje token dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="f9cd7-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9cd7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9cd7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f9cd7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9cd7-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="f9cd7-106">podczas Interfejs [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) , który reprezentuje zestaw, z którego zaimportowano typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="f9cd7-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f9cd7-107">podczas Tablica, która zawiera skrót dla zestawu określonego przez `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="f9cd7-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f9cd7-108">podczas Liczba bajtów w `pbHashValue` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9cd7-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="f9cd7-109">podczas Interfejs [IMetaDataImport](imetadataimport-interface.md) reprezentujący zakres metadanych, z którego jest importowany typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="f9cd7-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="f9cd7-110">podczas `mdTypeDef`Token określający typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="f9cd7-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="f9cd7-111">podczas Interfejs [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) , który reprezentuje zestaw, do którego zaimportowany jest typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="f9cd7-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f9cd7-112">określoną `mdTypeRef`Token, który jest zdefiniowany w bieżącym zakresie dla odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="f9cd7-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9cd7-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9cd7-113">Remarks</span></span>  
 <span data-ttu-id="f9cd7-114">Przed wywołaniem metody [IMetaDataEmit::D efineimportmember](imetadataemit-defineimportmember-method.md) , można użyć `DefineImportType` metody, aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej lub interfejsu nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f9cd7-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9cd7-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9cd7-115">Requirements</span></span>  
 <span data-ttu-id="f9cd7-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9cd7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9cd7-117">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f9cd7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9cd7-118">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f9cd7-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9cd7-119">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9cd7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9cd7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9cd7-120">See also</span></span>

- [<span data-ttu-id="f9cd7-121">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f9cd7-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f9cd7-122">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f9cd7-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
