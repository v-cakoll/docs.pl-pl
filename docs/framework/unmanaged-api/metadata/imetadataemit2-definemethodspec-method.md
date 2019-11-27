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
ms.openlocfilehash: 7547d7557169b1279125141afb5b05e22341942a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432743"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="b7bde-102">IMetaDataEmit2::DefineMethodSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7bde-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="b7bde-103">Tworzy wystąpienie ogólne metody i pobiera token do definicji.</span><span class="sxs-lookup"><span data-stu-id="b7bde-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7bde-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7bde-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7bde-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7bde-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="b7bde-106">podczas Token dla metody tworzenia wystąpienia ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b7bde-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="b7bde-107">Token musi być typu `mdMethodDef` lub `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="b7bde-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b7bde-108">podczas Wskaźnik do binarnego podpisu COM+ metody.</span><span class="sxs-lookup"><span data-stu-id="b7bde-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="b7bde-109">podczas Rozmiar w bajtach `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b7bde-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="b7bde-110">określoną Token do definicji sygnatury metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="b7bde-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7bde-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7bde-111">Requirements</span></span>  
 <span data-ttu-id="b7bde-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7bde-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7bde-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b7bde-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7bde-114">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b7bde-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7bde-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7bde-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7bde-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7bde-116">See also</span></span>

- [<span data-ttu-id="b7bde-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7bde-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="b7bde-118">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7bde-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
