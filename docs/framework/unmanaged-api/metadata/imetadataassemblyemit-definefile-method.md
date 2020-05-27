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
ms.openlocfilehash: 61d81c94e3a9c092b5d45791962635c761e8da8a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008147"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="a764e-102">IMetaDataAssemblyEmit::DefineFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="a764e-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="a764e-103">Tworzy `File` strukturę metadanych zawierającą metadane zestawu, do którego odwołuje się ten zestaw, i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="a764e-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a764e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a764e-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a764e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a764e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="a764e-106">podczas Nazwa pliku, który ma być użyty.</span><span class="sxs-lookup"><span data-stu-id="a764e-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="a764e-107">podczas Wskaźnik do danych skrótu skojarzonych z zestawem.</span><span class="sxs-lookup"><span data-stu-id="a764e-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="a764e-108">podczas Rozmiar w bajtach `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="a764e-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="a764e-109">podczas Bitowa kombinacja `FileFlags` wartości, które określają ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="a764e-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="a764e-110">określoną Wskaźnik do zwracanego `File` tokenu.</span><span class="sxs-lookup"><span data-stu-id="a764e-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a764e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a764e-111">Remarks</span></span>  
 <span data-ttu-id="a764e-112">`File`Dla każdego pliku, który był częścią tego zestawu, należy zdefiniować jedną strukturę metadanych, wykluczając plik zawierający metadane.</span><span class="sxs-lookup"><span data-stu-id="a764e-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a764e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a764e-113">Requirements</span></span>  
 <span data-ttu-id="a764e-114">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a764e-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a764e-115">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a764e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a764e-116">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a764e-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a764e-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a764e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a764e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a764e-118">See also</span></span>

- [<span data-ttu-id="a764e-119">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a764e-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
