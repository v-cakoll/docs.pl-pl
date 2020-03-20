---
title: IMetaDataImport::GetMemberRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175372"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="f3bd1-102">IMetaDataImport::GetMemberRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3bd1-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="f3bd1-103">Pobiera metadane skojarzone z elementem członkowskim, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3bd1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3bd1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,
   [out] mdToken           *ptk,
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3bd1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3bd1-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="f3bd1-106">[w] Token MemberRef do zwrócenia skojarzonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="f3bd1-107">[na zewnątrz] A TypeDef lub TypeRef lub TypeSpec token, który reprezentuje klasę, która deklaruje element członkowski lub ModułRef token, który reprezentuje klasę modułu, który deklaruje element członkowski lub MethodDef, który reprezentuje element członkowski.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="f3bd1-108">[na zewnątrz] Bufor ciągu dla nazwy członka.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="f3bd1-109">[w] Żądany rozmiar w szerokich znakach `szMember`.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="f3bd1-110">[na zewnątrz] Zwrócony rozmiar w `szMember`szerokich znakach .</span><span class="sxs-lookup"><span data-stu-id="f3bd1-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="f3bd1-111">[na zewnątrz] Wskaźnik do podpisu binarnych metadanych dla członka.</span><span class="sxs-lookup"><span data-stu-id="f3bd1-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="f3bd1-112">[na zewnątrz] Rozmiar w bajtach . `ppvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="f3bd1-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3bd1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3bd1-113">Requirements</span></span>  
 <span data-ttu-id="f3bd1-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3bd1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3bd1-115">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3bd1-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3bd1-116">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3bd1-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3bd1-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3bd1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bd1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3bd1-118">See also</span></span>

- [<span data-ttu-id="f3bd1-119">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f3bd1-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f3bd1-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3bd1-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
