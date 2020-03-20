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
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177869"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="0505c-102">IMetaDataAssemblyEmit::DefineManifestResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="0505c-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="0505c-103">Tworzy `ManifestResource` strukturę zawierającą metadane dla określonego zasobu manifestu i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="0505c-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0505c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0505c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0505c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0505c-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="0505c-106">[w] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="0505c-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="0505c-107">[w] Token metadanych `mdtFile` typu `mdtAssemblyRef` lub który jest mapowany do dostawcy zasobów.</span><span class="sxs-lookup"><span data-stu-id="0505c-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="0505c-108">Wartość NULL wskazuje, że plik, w którym osadzone są metadane, jest dostawcą zasobów.</span><span class="sxs-lookup"><span data-stu-id="0505c-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="0505c-109">[w] Przesunięcie na początek zasobu w pliku.</span><span class="sxs-lookup"><span data-stu-id="0505c-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="0505c-110">W przypadku zasobów w plikach autonomicznych zawsze będzie to zero.</span><span class="sxs-lookup"><span data-stu-id="0505c-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="0505c-111">Jeśli zasób jest osadzony w pliku PE (przenośny plik wykonywalny), jest to przesunięcie obiektu BLOB zasobu, który rozpoczyna się w lokalizacji określonej w pliku nagłówka cor.h.</span><span class="sxs-lookup"><span data-stu-id="0505c-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="0505c-112">[w] Bitowa kombinacja wartości flagi określających ustawienia właściwości dla definicji zasobu.</span><span class="sxs-lookup"><span data-stu-id="0505c-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="0505c-113">[na zewnątrz] Wskaźnik do zwróconego tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="0505c-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0505c-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0505c-114">Remarks</span></span>  
 <span data-ttu-id="0505c-115">Jedna `ManifestResource` struktura metadanych musi być zdefiniowana dla każdego zasobu, który jest implementowany w każdym pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="0505c-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0505c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0505c-116">Requirements</span></span>  
 <span data-ttu-id="0505c-117">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0505c-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0505c-118">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="0505c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0505c-119">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0505c-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0505c-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0505c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0505c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0505c-121">See also</span></span>

- [<span data-ttu-id="0505c-122">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0505c-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
