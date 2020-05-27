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
ms.openlocfilehash: 81d6c972b53221ee53cbcf31639d65c30858b48b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008160"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="08740-102">IMetaDataAssemblyEmit::DefineExportedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="08740-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="08740-103">Tworzy `ExportedType` strukturę zawierającą metadane dla określonego typu wyeksportowanego i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="08740-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08740-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08740-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08740-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08740-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="08740-106">podczas Nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="08740-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="08740-107">W przypadku wersji 1,1 środowiska uruchomieniowego języka wspólnego nazwa wyeksportowanego typu musi być dokładnie zgodna z nazwą podaną w `TypeDef` dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="08740-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="08740-108">podczas Token określający, gdzie jest zaimplementowany wyeksportowany typ.</span><span class="sxs-lookup"><span data-stu-id="08740-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="08740-109">Prawidłowe wartości i ich powiązane znaczenie są następujące:</span><span class="sxs-lookup"><span data-stu-id="08740-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="08740-110">`mdFile`Typ jest zaimplementowany w innym pliku w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="08740-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="08740-111">`mdAssemblyRef`Typ jest zaimplementowany w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="08740-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="08740-112">`mdExportedTYpe`Typ jest zagnieżdżony w innym typie.</span><span class="sxs-lookup"><span data-stu-id="08740-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="08740-113">`mdFileNil`Typ znajduje się w tym samym pliku co manifest i nie jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="08740-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="08740-114">podczas Token do metadanych, który określa typ do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="08740-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="08740-115">Ta wartość jest wprowadzana w `TypeDef` tabeli w pliku, który implementuje typ i ma zastosowanie tylko wtedy, gdy ten plik znajduje się w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="08740-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="08740-116">podczas Bitowa kombinacja wartości wyliczenia [CorTypeAttr —](cortypeattr-enumeration.md) , które definiują ustawienia właściwości dla wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="08740-116">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="08740-117">określoną Wskaźnik do zwracanego tokenu metadanych, który wskazuje wyeksportowany typ.</span><span class="sxs-lookup"><span data-stu-id="08740-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08740-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08740-118">Remarks</span></span>  
 <span data-ttu-id="08740-119">`ExportedType`Dla każdego typu, który jest udostępniany przez ten zestaw, musi być zdefiniowana Struktura metadanych, która jest zaimplementowana w module innym niż ten, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="08740-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08740-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08740-120">Requirements</span></span>  
 <span data-ttu-id="08740-121">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08740-121">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08740-122">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="08740-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08740-123">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08740-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08740-124">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08740-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08740-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08740-125">See also</span></span>

- [<span data-ttu-id="08740-126">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="08740-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
