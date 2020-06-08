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
ms.openlocfilehash: 00693f1a87334620442e8865e76183b2dab68878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503620"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="84074-102">IMetaDataImport::GetMemberRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="84074-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="84074-103">Pobiera metadane skojarzone z elementem członkowskim, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="84074-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84074-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84074-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="84074-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84074-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="84074-106">podczas Token elementu MemberRef do zwrócenia skojarzonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="84074-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="84074-107">określoną Element TypeDef lub TypeRef albo token elementu TypeSpec reprezentujący klasę, która deklaruje element członkowski lub token elementu ModuleRef reprezentujący klasę modułu, która deklaruje element członkowski, lub element MethodDef reprezentujący element członkowski.</span><span class="sxs-lookup"><span data-stu-id="84074-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="84074-108">określoną Bufor ciągu dla nazwy elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="84074-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="84074-109">podczas Żądany rozmiar w postaci znaków dwubajtowych `szMember` .</span><span class="sxs-lookup"><span data-stu-id="84074-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="84074-110">określoną Zwrócony rozmiar w postaci znaków dwubajtowych `szMember` .</span><span class="sxs-lookup"><span data-stu-id="84074-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="84074-111">określoną Wskaźnik do binarnego podpisu metadanych dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="84074-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="84074-112">określoną Rozmiar w bajtach `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="84074-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84074-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84074-113">Requirements</span></span>  
 <span data-ttu-id="84074-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84074-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84074-115">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="84074-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84074-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="84074-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84074-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84074-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84074-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84074-118">See also</span></span>

- [<span data-ttu-id="84074-119">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="84074-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="84074-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="84074-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
