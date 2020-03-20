---
title: IMetaDataEmit::DefineUserString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: a71d8694ec8c5bd35ecd3e98ed32e05bc7b382fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177615"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="ba47a-102">IMetaDataEmit::DefineUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba47a-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="ba47a-103">Pobiera token metadanych dla określonego ciągu literału.</span><span class="sxs-lookup"><span data-stu-id="ba47a-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba47a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba47a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba47a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba47a-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="ba47a-106">[w] Ciąg użytkownika do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="ba47a-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="ba47a-107">[w] Liczba szerokich znaków `szString`w pliku .</span><span class="sxs-lookup"><span data-stu-id="ba47a-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="ba47a-108">[na zewnątrz] Przypisany token ciągu.</span><span class="sxs-lookup"><span data-stu-id="ba47a-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba47a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba47a-109">Requirements</span></span>  
 <span data-ttu-id="ba47a-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba47a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba47a-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ba47a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba47a-112">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba47a-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba47a-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba47a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba47a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba47a-114">See also</span></span>

- [<span data-ttu-id="ba47a-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ba47a-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ba47a-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba47a-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
