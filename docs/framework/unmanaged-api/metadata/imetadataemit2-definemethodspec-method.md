---
title: IMetaDataEmit2::DefineMethodSpec — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d56209e030939f53e3f72fe0c8a10db2160dd19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492523"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="9028e-102">IMetaDataEmit2::DefineMethodSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="9028e-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="9028e-103">Tworzy wystąpienia ogólnego metody, a następnie pobiera token do definicji.</span><span class="sxs-lookup"><span data-stu-id="9028e-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9028e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9028e-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9028e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9028e-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="9028e-106">[in] Token dla metody, której chcesz utworzyć wystąpienia ogólnego.</span><span class="sxs-lookup"><span data-stu-id="9028e-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="9028e-107">Token musi być typu `mdMethodDef` lub `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="9028e-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="9028e-108">[in] Wskaźnik do binarnych modelu COM + podpis metody.</span><span class="sxs-lookup"><span data-stu-id="9028e-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="9028e-109">[in] Rozmiar w bajtach z `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="9028e-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="9028e-110">[out] Token do definicji metadanych podpis metody.</span><span class="sxs-lookup"><span data-stu-id="9028e-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9028e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9028e-111">Requirements</span></span>  
 <span data-ttu-id="9028e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9028e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9028e-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9028e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9028e-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9028e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9028e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9028e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9028e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9028e-116">See also</span></span>
- [<span data-ttu-id="9028e-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9028e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="9028e-118">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="9028e-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
