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
ms.openlocfilehash: a5d9342b8bfe650106ccf9daf2a91dfbcd575446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175542"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="3a0da-102">IMetaDataEmit2::DefineMethodSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a0da-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="3a0da-103">Tworzy ogólne wystąpienie metody i pobiera token do definicji.</span><span class="sxs-lookup"><span data-stu-id="3a0da-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a0da-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a0da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a0da-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="3a0da-106">[w] Token dla metody, której można utworzyć wystąpienie ogólne.</span><span class="sxs-lookup"><span data-stu-id="3a0da-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="3a0da-107">Token musi być `mdMethodDef` typu `mdMemberRef`lub .</span><span class="sxs-lookup"><span data-stu-id="3a0da-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3a0da-108">[w] Wskaźnik do binarnego sygnatury COM+ metody.</span><span class="sxs-lookup"><span data-stu-id="3a0da-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="3a0da-109">[w] Rozmiar w bajtach `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="3a0da-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="3a0da-110">[na zewnątrz] Token do definicji podpisu metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="3a0da-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a0da-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a0da-111">Requirements</span></span>  
 <span data-ttu-id="3a0da-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a0da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a0da-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a0da-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a0da-114">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a0da-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a0da-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a0da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a0da-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a0da-116">See also</span></span>

- [<span data-ttu-id="3a0da-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a0da-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="3a0da-118">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3a0da-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
