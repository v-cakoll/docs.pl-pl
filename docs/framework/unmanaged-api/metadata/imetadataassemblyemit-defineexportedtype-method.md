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
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177879"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="97d12-102">IMetaDataAssemblyEmit::DefineExportedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="97d12-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="97d12-103">Tworzy `ExportedType` strukturę zawierającą metadane dla określonego typu eksportowanego i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="97d12-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d12-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97d12-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97d12-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97d12-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="97d12-106">[w] Nazwa typu, który ma zostać wyeksportowany.</span><span class="sxs-lookup"><span data-stu-id="97d12-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="97d12-107">W przypadku wersji 1.1 środowiska wykonawczego języka wspólnego nazwa eksportowanego typu musi dokładnie `TypeDef` odpowiadać nazwie podanej w dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="97d12-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="97d12-108">[w] Token określający, gdzie jest implementowany typ eksportowany.</span><span class="sxs-lookup"><span data-stu-id="97d12-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="97d12-109">Prawidłowe wartości i związane z nimi znaczenie to:</span><span class="sxs-lookup"><span data-stu-id="97d12-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="97d12-110">`mdFile`Typ jest implementowany w innym pliku w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="97d12-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="97d12-111">`mdAssemblyRef`Typ jest implementowany w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="97d12-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="97d12-112">`mdExportedTYpe`Typ jest zagnieżdżony w ramach innego typu.</span><span class="sxs-lookup"><span data-stu-id="97d12-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="97d12-113">`mdFileNil`Typ znajduje się w tym samym pliku co manifest i nie jest typem zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="97d12-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="97d12-114">[w] Token do metadanych, który określa typ do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="97d12-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="97d12-115">Ta wartość jest wprowadzana w `TypeDef` tabeli w pliku, który implementuje typ i jest istotne tylko wtedy, gdy ten plik znajduje się w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="97d12-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="97d12-116">[w] Bitowa kombinacja wartości wyliczenia [CorTypeAttr,](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) które definiują ustawienia właściwości dla eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="97d12-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="97d12-117">[na zewnątrz] Wskaźnik do zwróconego tokenu metadanych, który wskazuje eksportowany typ.</span><span class="sxs-lookup"><span data-stu-id="97d12-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97d12-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97d12-118">Remarks</span></span>  
 <span data-ttu-id="97d12-119">Struktura `ExportedType` metadanych musi być zdefiniowana dla każdego typu, który jest widoczna przez ten zestaw i który jest implementowany w module innym niż ten zawierający manifest.</span><span class="sxs-lookup"><span data-stu-id="97d12-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d12-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97d12-120">Requirements</span></span>  
 <span data-ttu-id="97d12-121">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97d12-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d12-122">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="97d12-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97d12-123">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97d12-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97d12-124">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d12-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d12-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97d12-125">See also</span></span>

- [<span data-ttu-id="97d12-126">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="97d12-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
