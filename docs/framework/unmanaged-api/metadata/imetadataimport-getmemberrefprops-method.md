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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbc297ce129ba223d85b5e13da1f046b3010f4d3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466027"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="df06e-102">IMetaDataImport::GetMemberRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="df06e-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="df06e-103">Pobiera metadane skojarzone z elementem członkowskim odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="df06e-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df06e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df06e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="df06e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df06e-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="df06e-106">[in] Token MemberRef do zwrócenia skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="df06e-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="df06e-107">[out] Token TypeDef TypeRef i/lub elementu TypeSpec, który reprezentuje klasę, która deklaruje element członkowski lub token element ModuleRef, który reprezentuje klasę modułu, która deklaruje element członkowski lub MethodDef, który reprezentuje element członkowski.</span><span class="sxs-lookup"><span data-stu-id="df06e-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="df06e-108">[out] Buforu ciągu dla nazwy elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="df06e-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="df06e-109">[in] Żądany rozmiar w znaków `szMember`.</span><span class="sxs-lookup"><span data-stu-id="df06e-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="df06e-110">[out] Rozmiar zwrócony w znaków `szMember`.</span><span class="sxs-lookup"><span data-stu-id="df06e-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="df06e-111">[out] Wskaźnik do podpisu metadanych binarnych dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="df06e-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="df06e-112">[out] Rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="df06e-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df06e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df06e-113">Requirements</span></span>  
 <span data-ttu-id="df06e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df06e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df06e-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="df06e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df06e-116">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df06e-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df06e-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df06e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df06e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df06e-118">See also</span></span>
- [<span data-ttu-id="df06e-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="df06e-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="df06e-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="df06e-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
