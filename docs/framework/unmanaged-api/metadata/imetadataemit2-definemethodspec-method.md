---
title: "IMetaDataEmit2::DefineMethodSpec — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineMethodSpec
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 036654c733dc73d40c526bf5cad4dd3750e2e9d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="b803b-102">IMetaDataEmit2::DefineMethodSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="b803b-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="b803b-103">Tworzy wystąpienie ogólnego metody i pobiera token do definicji.</span><span class="sxs-lookup"><span data-stu-id="b803b-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b803b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b803b-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b803b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b803b-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="b803b-106">[in] Token metody, których można utworzyć wystąpienia ogólnych.</span><span class="sxs-lookup"><span data-stu-id="b803b-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="b803b-107">Token musi być typu `mdMethodDef` lub `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="b803b-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b803b-108">[in] Wskaźnik do binarnego COM + podpis metody.</span><span class="sxs-lookup"><span data-stu-id="b803b-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="b803b-109">[in] Rozmiar w bajtach z `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b803b-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="b803b-110">[out] Token do definicji metadanych podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="b803b-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b803b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b803b-111">Requirements</span></span>  
 <span data-ttu-id="b803b-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b803b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b803b-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b803b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b803b-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b803b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b803b-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b803b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b803b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b803b-116">See Also</span></span>  
 [<span data-ttu-id="b803b-117">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b803b-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="b803b-118">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="b803b-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
