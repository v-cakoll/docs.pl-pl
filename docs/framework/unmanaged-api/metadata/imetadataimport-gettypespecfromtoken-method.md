---
title: IMetaDataImport::GetTypeSpecFromToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
ms.openlocfilehash: 34b7cebfa063a3ad077b74a753fd37ba67ff53a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175320"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="12ce6-102">IMetaDataImport::GetTypeSpecFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="12ce6-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="12ce6-103">Pobiera podpis metadanych binarnych specyfikacji typu reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="12ce6-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ce6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12ce6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12ce6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12ce6-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="12ce6-106">[w] Token TypeSpec skojarzony z żądanym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="12ce6-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="12ce6-107">[na zewnątrz] Wskaźnik do podpisu metadanych binarnych.</span><span class="sxs-lookup"><span data-stu-id="12ce6-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="12ce6-108">[na zewnątrz] Rozmiar w bajtach podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="12ce6-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12ce6-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="12ce6-109">Return Value</span></span>  
 <span data-ttu-id="12ce6-110">HRESULT, który wskazuje na sukces lub porażkę.</span><span class="sxs-lookup"><span data-stu-id="12ce6-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="12ce6-111">Błędy można przetestować za pomocą makra FAILED.</span><span class="sxs-lookup"><span data-stu-id="12ce6-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12ce6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12ce6-112">Requirements</span></span>  
 <span data-ttu-id="12ce6-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12ce6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ce6-114">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="12ce6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12ce6-115">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12ce6-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12ce6-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12ce6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ce6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12ce6-117">See also</span></span>

- [<span data-ttu-id="12ce6-118">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="12ce6-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="12ce6-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="12ce6-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
