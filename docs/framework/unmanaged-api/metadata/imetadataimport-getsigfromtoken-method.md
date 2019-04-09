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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 823a172c05d2ce76fef790966f54d7216f579fde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152987"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="7f5d9-102">IMetaDataImport::GetSigFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f5d9-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="7f5d9-103">Pobiera podpisu binarne metadane skojarzone z określonym tokenem.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f5d9-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f5d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f5d9-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="7f5d9-106">[in] Token, który zwraca podpis binarne metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="7f5d9-107">[out] Wskaźnik do podpisu zwróconych metadanych.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="7f5d9-108">[out] Rozmiar w bajtach sygnatura binarne metadanych.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f5d9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f5d9-109">Requirements</span></span>  
 <span data-ttu-id="7f5d9-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f5d9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f5d9-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7f5d9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f5d9-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f5d9-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7f5d9-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7f5d9-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f5d9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f5d9-114">See also</span></span>

- [<span data-ttu-id="7f5d9-115">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7f5d9-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7f5d9-116">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7f5d9-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
