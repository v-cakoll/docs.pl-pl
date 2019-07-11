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
ms.openlocfilehash: a4185ec41fc9f7d1d919a79b57c02625210ad72a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777183"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="30fdb-102">IMetaDataEmit2::DefineMethodSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="30fdb-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="30fdb-103">Tworzy wystąpienia ogólnego metody, a następnie pobiera token do definicji.</span><span class="sxs-lookup"><span data-stu-id="30fdb-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30fdb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30fdb-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30fdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30fdb-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="30fdb-106">[in] Token dla metody, której chcesz utworzyć wystąpienia ogólnego.</span><span class="sxs-lookup"><span data-stu-id="30fdb-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="30fdb-107">Token musi być typu `mdMethodDef` lub `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="30fdb-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="30fdb-108">[in] Wskaźnik do binarnych modelu COM + podpis metody.</span><span class="sxs-lookup"><span data-stu-id="30fdb-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="30fdb-109">[in] Rozmiar w bajtach z `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="30fdb-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="30fdb-110">[out] Token do definicji metadanych podpis metody.</span><span class="sxs-lookup"><span data-stu-id="30fdb-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30fdb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30fdb-111">Requirements</span></span>  
 <span data-ttu-id="30fdb-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30fdb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30fdb-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="30fdb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30fdb-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30fdb-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30fdb-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30fdb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30fdb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30fdb-116">See also</span></span>

- [<span data-ttu-id="30fdb-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="30fdb-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="30fdb-118">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="30fdb-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
