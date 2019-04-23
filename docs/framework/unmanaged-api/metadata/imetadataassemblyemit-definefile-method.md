---
title: IMetaDataAssemblyEmit::DefineFile — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5693da3b5e6d883efd9ad8a5a409a5dba8dd8b6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203434"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="86389-102">IMetaDataAssemblyEmit::DefineFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="86389-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="86389-103">Tworzy `File` struktury metadanych zawierający metadane zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="86389-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86389-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86389-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86389-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86389-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="86389-106">[in] Nazwa pliku do użycia.</span><span class="sxs-lookup"><span data-stu-id="86389-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="86389-107">[in] Wskaźnik do danych wyznaczania wartości skrótu, skojarzone z zestawem.</span><span class="sxs-lookup"><span data-stu-id="86389-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="86389-108">[in] Rozmiar w bajtach `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="86389-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="86389-109">[in] Bitowa kombinacja `FileFlags` wartości, które określają ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="86389-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="86389-110">[out] Wskaźnik do zwracanego `File` tokenu.</span><span class="sxs-lookup"><span data-stu-id="86389-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86389-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86389-111">Remarks</span></span>  
 <span data-ttu-id="86389-112">Jeden `File` struktury metadanych musi być zdefiniowana dla każdego pliku, które było częścią tego zestawu w czasie, który został zbudowany tego zestawu, z wyjątkiem pliku który zawiera metadane.</span><span class="sxs-lookup"><span data-stu-id="86389-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86389-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86389-113">Requirements</span></span>  
 <span data-ttu-id="86389-114">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86389-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86389-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="86389-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86389-116">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86389-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86389-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86389-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86389-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86389-118">See also</span></span>

- [<span data-ttu-id="86389-119">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="86389-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
