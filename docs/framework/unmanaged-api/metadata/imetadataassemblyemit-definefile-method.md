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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203434"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="f594c-102">IMetaDataAssemblyEmit::DefineFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="f594c-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="f594c-103">Tworzy `File` struktury metadanych zawierający metadane zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="f594c-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f594c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f594c-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f594c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f594c-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f594c-106">[in] Nazwa pliku do użycia.</span><span class="sxs-lookup"><span data-stu-id="f594c-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f594c-107">[in] Wskaźnik do danych wyznaczania wartości skrótu, skojarzone z zestawem.</span><span class="sxs-lookup"><span data-stu-id="f594c-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f594c-108">[in] Rozmiar w bajtach `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f594c-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="f594c-109">[in] Bitowa kombinacja `FileFlags` wartości, które określają ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="f594c-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="f594c-110">[out] Wskaźnik do zwracanego `File` tokenu.</span><span class="sxs-lookup"><span data-stu-id="f594c-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f594c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f594c-111">Remarks</span></span>  
 <span data-ttu-id="f594c-112">Jeden `File` struktury metadanych musi być zdefiniowana dla każdego pliku, które było częścią tego zestawu w czasie, który został zbudowany tego zestawu, z wyjątkiem pliku który zawiera metadane.</span><span class="sxs-lookup"><span data-stu-id="f594c-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f594c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f594c-113">Requirements</span></span>  
 <span data-ttu-id="f594c-114">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f594c-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f594c-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f594c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f594c-116">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f594c-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f594c-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f594c-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f594c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f594c-118">See also</span></span>

- [<span data-ttu-id="f594c-119">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f594c-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
