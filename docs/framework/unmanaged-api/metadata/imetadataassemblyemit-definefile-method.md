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
ms.openlocfilehash: 46fa6ab3ea4a63583b01ffe25d22840301613100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444799"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="f8658-102">IMetaDataAssemblyEmit::DefineFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8658-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="f8658-103">Tworzy `File` struktury metadane zawierające metadanych dla zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="f8658-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8658-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8658-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8658-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8658-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f8658-106">[in] Nazwa pliku, który ma być używane.</span><span class="sxs-lookup"><span data-stu-id="f8658-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f8658-107">[in] Wskaźnik do wyznaczania wartości skrótu skojarzonych z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="f8658-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f8658-108">[in] Wyrażony w bajtach rozmiar `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f8658-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="f8658-109">[in] Bitowe połączenie `FileFlags` wartości, które określają ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8658-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="f8658-110">[out] Wskaźnik do zwróconego `File` tokenu.</span><span class="sxs-lookup"><span data-stu-id="f8658-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8658-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8658-111">Remarks</span></span>  
 <span data-ttu-id="f8658-112">Jeden `File` struktura metadanych musi być zdefiniowana dla każdego pliku, który jest częścią tego zestawu w czasie ten zestaw został utworzony, wyłączając plik zawierający metadane.</span><span class="sxs-lookup"><span data-stu-id="f8658-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8658-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8658-113">Requirements</span></span>  
 <span data-ttu-id="f8658-114">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8658-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8658-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f8658-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8658-116">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8658-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8658-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8658-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8658-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8658-118">See Also</span></span>  
 [<span data-ttu-id="f8658-119">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8658-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
