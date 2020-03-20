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
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176061"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="00d94-102">IMetaDataAssemblyEmit::DefineFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="00d94-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="00d94-103">Tworzy `File` strukturę metadanych zawierającą metadane dla zestawu, do którego odwołuje się ten zestaw, i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="00d94-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00d94-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00d94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00d94-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="00d94-106">[w] Nazwa pliku, który ma zostać zużyty.</span><span class="sxs-lookup"><span data-stu-id="00d94-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="00d94-107">[w] Wskaźnik do danych mieszania skojarzonych z zestawem.</span><span class="sxs-lookup"><span data-stu-id="00d94-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="00d94-108">[w] Rozmiar w bajtach . `pbHashValue`</span><span class="sxs-lookup"><span data-stu-id="00d94-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="00d94-109">[w] Bitowa kombinacja `FileFlags` wartości określających ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="00d94-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="00d94-110">[na zewnątrz] Wskaźnik do zwróconego `File` tokenu.</span><span class="sxs-lookup"><span data-stu-id="00d94-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00d94-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00d94-111">Remarks</span></span>  
 <span data-ttu-id="00d94-112">Jedna `File` struktura metadanych musi być zdefiniowana dla każdego pliku, który był częścią tego zestawu w czasie, gdy ten zestaw został zbudowany, z wyłączeniem pliku, który zawiera metadane.</span><span class="sxs-lookup"><span data-stu-id="00d94-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d94-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00d94-113">Requirements</span></span>  
 <span data-ttu-id="00d94-114">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d94-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d94-115">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="00d94-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00d94-116">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00d94-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00d94-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d94-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d94-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00d94-118">See also</span></span>

- [<span data-ttu-id="00d94-119">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="00d94-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
