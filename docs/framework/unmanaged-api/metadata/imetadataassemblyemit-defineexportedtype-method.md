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
ms.openlocfilehash: 5702fac139ba602828bb8722a1e3e25d6f1c58f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625437"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="5e486-102">IMetaDataAssemblyEmit::DefineExportedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e486-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="5e486-103">Tworzy `ExportedType` struktury zawierającej metadanych dla określonego wyeksportować typu, a następnie zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="5e486-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e486-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e486-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e486-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e486-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="5e486-106">[in] Nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="5e486-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="5e486-107">Dla wersji 1.1 środowisko uruchomieniowe języka wspólnego, nazwa typu wyeksportowanego musi dokładnie odpowiadać nazwa nadana `TypeDef` dla typu.</span><span class="sxs-lookup"><span data-stu-id="5e486-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="5e486-108">[in] Token, określający, gdzie typ eksportowany jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="5e486-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="5e486-109">Prawidłowe wartości i ich znaczenie skojarzone są:</span><span class="sxs-lookup"><span data-stu-id="5e486-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="5e486-110">`mdFile` Typ jest zaimplementowana w innym pliku w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="5e486-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="5e486-111">`mdAssemblyRef` Typ jest zaimplementowana w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="5e486-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="5e486-112">`mdExportedTYpe` Typ jest zagnieżdżony w ramach innego typu.</span><span class="sxs-lookup"><span data-stu-id="5e486-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="5e486-113">`mdFileNil` Typ znajduje się w tym samym pliku manifestu i nie jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="5e486-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="5e486-114">[in] Token metadanych, który określa typ do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="5e486-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="5e486-115">Ta wartość jest wprowadzana w `TypeDef` tabeli w pliku, który implementuje ten typ. i ma zastosowanie tylko wtedy, gdy ten plik znajduje się w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="5e486-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="5e486-116">[in] Bitowa kombinacja [cortypeattr —](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wartości wyliczenia, które definiują ustawienia właściwości typu wyeksportowanego.</span><span class="sxs-lookup"><span data-stu-id="5e486-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="5e486-117">[out] Wskaźnik do tokenu zwróconych metadanych, który określa typ eksportowany.</span><span class="sxs-lookup"><span data-stu-id="5e486-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e486-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e486-118">Remarks</span></span>  
 <span data-ttu-id="5e486-119">`ExportedType` Struktury metadanych musi być zdefiniowana dla każdego typu, który jest udostępniany przez ten zestaw i jest implementowana w module innym niż zawierającego manifest.</span><span class="sxs-lookup"><span data-stu-id="5e486-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e486-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e486-120">Requirements</span></span>  
 <span data-ttu-id="5e486-121">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e486-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e486-122">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5e486-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e486-123">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e486-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e486-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e486-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e486-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e486-125">See also</span></span>

- [<span data-ttu-id="5e486-126">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e486-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
