---
title: IMetaDataAssemblyEmit::DefineExportedType — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2eb894a8bac702c30826d1e965c91cae9b259ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448563"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="cf3bd-102">IMetaDataAssemblyEmit::DefineExportedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf3bd-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="cf3bd-103">Tworzy `ExportedType` struktury zawierający metadane dla określonej wyeksportowanego typu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf3bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf3bd-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf3bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf3bd-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="cf3bd-106">[in] Nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="cf3bd-107">Dla środowiska CLR, nazwa typu wyeksportowanego w wersji 1.1 musi dokładnie odpowiadać nazwie podanej w `TypeDef` dla typu.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="cf3bd-108">[in] Token określający, gdzie wyeksportowanego typu jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="cf3bd-109">Prawidłowe wartości i ich znaczenie skojarzone są:</span><span class="sxs-lookup"><span data-stu-id="cf3bd-109">The valid values and their associated meanings are:</span></span>  
  
-   <span data-ttu-id="cf3bd-110">`mdFile` Typ jest zaimplementowana w innym pliku w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
-   <span data-ttu-id="cf3bd-111">`mdAssemblyRef` Typ jest zaimplementowana w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
-   <span data-ttu-id="cf3bd-112">`mdExportedTYpe` Typ jest zagnieżdżony w ramach innego typu.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
-   <span data-ttu-id="cf3bd-113">`mdFileNil` Typ jest w tym samym pliku jako manifest i nie jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="cf3bd-114">[in] Token określający typ do wyeksportowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="cf3bd-115">Ta wartość jest wprowadzana w `TypeDef` tabeli w pliku, który implementuje typ i ma zastosowanie tylko wtedy, gdy ten plik jest w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="cf3bd-116">[in] Bitowe połączenie [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wartości wyliczenia, które definiują ustawienia właściwości wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="cf3bd-117">[out] Wskaźnik do tokenu zwrócone metadane, który wskazuje wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf3bd-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf3bd-118">Remarks</span></span>  
 <span data-ttu-id="cf3bd-119">`ExportedType` Struktura metadanych musi być zdefiniowana dla każdego typu, który jest udostępniany przez ten zestaw i wykonywane w module innego niż ten, zawierający manifestu.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf3bd-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf3bd-120">Requirements</span></span>  
 <span data-ttu-id="cf3bd-121">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf3bd-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf3bd-122">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf3bd-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf3bd-123">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf3bd-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf3bd-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf3bd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf3bd-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf3bd-125">See Also</span></span>  
 [<span data-ttu-id="cf3bd-126">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf3bd-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
