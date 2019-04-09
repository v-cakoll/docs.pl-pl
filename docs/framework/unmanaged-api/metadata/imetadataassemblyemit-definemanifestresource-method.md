---
title: IMetaDataAssemblyEmit::DefineManifestResource — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b617e29e2df22b59114c8b978daa645de1cc6176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186722"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="f628b-102">IMetaDataAssemblyEmit::DefineManifestResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="f628b-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="f628b-103">Tworzy `ManifestResource` struktury zawierającymi metadane dla określonego zasobu manifestu, a następnie zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="f628b-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f628b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f628b-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f628b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f628b-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f628b-106">[in] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="f628b-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="f628b-107">[in] Token metadanych typu `mdtFile` lub `mdtAssemblyRef` która jest mapowana na potrzeby dostawcy zasobów.</span><span class="sxs-lookup"><span data-stu-id="f628b-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="f628b-108">Wartość NULL wskazuje plik, w której jest osadzony metadanych dostawcy zasobów.</span><span class="sxs-lookup"><span data-stu-id="f628b-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="f628b-109">[in] Przesunięcie początku zasobu w pliku.</span><span class="sxs-lookup"><span data-stu-id="f628b-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="f628b-110">Dla zasobów w plikach autonomicznego ta będzie zawsze równa zero.</span><span class="sxs-lookup"><span data-stu-id="f628b-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="f628b-111">Jeśli zasób jest osadzony w pliku PE (przenośny plik wykonywalny), to przesunięcie obiektu BLOB, który rozpoczyna się w lokalizacji określonej w pliku nagłówkowym cor.h zasobu.</span><span class="sxs-lookup"><span data-stu-id="f628b-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="f628b-112">[in] Bitowa kombinacja wartości flagi, które określają ustawienia właściwości definicji zasobu.</span><span class="sxs-lookup"><span data-stu-id="f628b-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="f628b-113">[out] Wskaźnik do tokenu zwróconych metadanych.</span><span class="sxs-lookup"><span data-stu-id="f628b-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f628b-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f628b-114">Remarks</span></span>  
 <span data-ttu-id="f628b-115">Jeden `ManifestResource` struktury metadanych musi być zdefiniowana dla każdego zasobu, który jest implementowany w każdym z plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="f628b-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f628b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f628b-116">Requirements</span></span>  
 <span data-ttu-id="f628b-117">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f628b-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f628b-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f628b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f628b-119">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f628b-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f628b-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f628b-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f628b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f628b-121">See also</span></span>

- [<span data-ttu-id="f628b-122">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f628b-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
