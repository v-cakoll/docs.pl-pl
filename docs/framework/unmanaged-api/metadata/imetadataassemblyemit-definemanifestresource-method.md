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
ms.openlocfilehash: 026f5efe195cdb34999b65c5f47de6f68d30e11a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008134"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="31825-102">IMetaDataAssemblyEmit::DefineManifestResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="31825-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="31825-103">Tworzy `ManifestResource` strukturę zawierającą metadane dla określonego zasobu manifestu i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="31825-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31825-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31825-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31825-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31825-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="31825-106">podczas Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="31825-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="31825-107">podczas Token metadanych typu `mdtFile` lub `mdtAssemblyRef` mapowany do dostawcy zasobów.</span><span class="sxs-lookup"><span data-stu-id="31825-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="31825-108">Wartość NULL wskazuje, że plik, w którym są osadzone metadane, jest dostawcą zasobów.</span><span class="sxs-lookup"><span data-stu-id="31825-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="31825-109">podczas Przesunięcie do początku zasobu w pliku.</span><span class="sxs-lookup"><span data-stu-id="31825-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="31825-110">W przypadku zasobów w plikach autonomicznych zawsze będzie to zero.</span><span class="sxs-lookup"><span data-stu-id="31825-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="31825-111">Jeśli zasób jest osadzony w pliku PE (przenośny plik wykonywalny), jest to przesunięcie obiektu BLOB zasobu, który jest uruchamiany w lokalizacji określonej w pliku nagłówkowym cor. h.</span><span class="sxs-lookup"><span data-stu-id="31825-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="31825-112">podczas Bitowa kombinacja wartości flag, które określają ustawienia właściwości dla definicji zasobu.</span><span class="sxs-lookup"><span data-stu-id="31825-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="31825-113">określoną Wskaźnik do zwracanego tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="31825-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31825-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31825-114">Remarks</span></span>  
 <span data-ttu-id="31825-115">`ManifestResource`Dla każdego zasobu, który jest zaimplementowany w każdym z plików zestawu, musi być zdefiniowana jedna struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="31825-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31825-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31825-116">Requirements</span></span>  
 <span data-ttu-id="31825-117">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31825-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31825-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="31825-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31825-119">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="31825-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31825-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31825-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31825-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31825-121">See also</span></span>

- [<span data-ttu-id="31825-122">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="31825-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
