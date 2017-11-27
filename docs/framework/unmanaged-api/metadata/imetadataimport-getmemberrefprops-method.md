---
title: "IMetaDataImport::GetMemberRefProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0b4b0399c22890226ad49ca0f3a5c709fb251653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="888a9-102">IMetaDataImport::GetMemberRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="888a9-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="888a9-103">Pobiera metadane skojarzone z elementem członkowskim odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="888a9-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="888a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="888a9-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="888a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="888a9-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="888a9-106">[in] Token elementu MemberRef do zwrócenia skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="888a9-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="888a9-107">[out] Token TypeDef lub TypeRef lub elementu TypeSpec, który reprezentuje klasę, która deklaruje element członkowski lub element ModuleRef token, który reprezentuje klasę moduł, który deklaruje element członkowski lub MethodDef, który reprezentuje element członkowski.</span><span class="sxs-lookup"><span data-stu-id="888a9-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="888a9-108">[out] Buforu ciągu dla nazwy elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="888a9-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="888a9-109">[in] Żądany rozmiar w znaki dwubajtowe `szMember`.</span><span class="sxs-lookup"><span data-stu-id="888a9-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="888a9-110">[out] Rozmiar zwróconego w znaki dwubajtowe `szMember`.</span><span class="sxs-lookup"><span data-stu-id="888a9-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="888a9-111">[out] Wskaźnik do podpisu metadanych binarnych dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="888a9-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="888a9-112">[out] Wyrażony w bajtach rozmiar `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="888a9-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="888a9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="888a9-113">Requirements</span></span>  
 <span data-ttu-id="888a9-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="888a9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="888a9-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="888a9-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="888a9-116">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="888a9-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="888a9-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="888a9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888a9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="888a9-118">See Also</span></span>  
 [<span data-ttu-id="888a9-119">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="888a9-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="888a9-120">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="888a9-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
