---
title: IMetaDataImport::GetSigFromToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
ms.openlocfilehash: 205f48fb417365565695c72095187d349127e536
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436847"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="b0efe-102">IMetaDataImport::GetSigFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0efe-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="b0efe-103">Gets the binary metadata signature associated with the specified token.</span><span class="sxs-lookup"><span data-stu-id="b0efe-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0efe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0efe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0efe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0efe-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="b0efe-106">[in] The token to return the binary metadata signature for.</span><span class="sxs-lookup"><span data-stu-id="b0efe-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="b0efe-107">[out] A pointer to the returned metadata signature.</span><span class="sxs-lookup"><span data-stu-id="b0efe-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="b0efe-108">[out] The size in bytes of the binary metadata signature.</span><span class="sxs-lookup"><span data-stu-id="b0efe-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0efe-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0efe-109">Requirements</span></span>  
 <span data-ttu-id="b0efe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0efe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0efe-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b0efe-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0efe-112">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0efe-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0efe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0efe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0efe-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0efe-114">See also</span></span>

- [<span data-ttu-id="b0efe-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0efe-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b0efe-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0efe-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
