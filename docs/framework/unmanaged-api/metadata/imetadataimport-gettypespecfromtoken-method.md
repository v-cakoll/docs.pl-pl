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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53d0f3bd991d502e4ddcad7df1e24d18af367e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598397"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="2b719-102">IMetaDataImport::GetTypeSpecFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b719-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="2b719-103">Pobiera podpisu metadanych binarne specyfikacji typu reprezentowanego przez określony token.</span><span class="sxs-lookup"><span data-stu-id="2b719-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b719-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b719-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b719-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b719-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="2b719-106">[in] Token elementu TypeSpec związany z podpisem żądanego metadanych.</span><span class="sxs-lookup"><span data-stu-id="2b719-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="2b719-107">[out] Wskaźnik do podpisu metadanych binarnego.</span><span class="sxs-lookup"><span data-stu-id="2b719-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="2b719-108">[out] Rozmiar w bajtach podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2b719-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b719-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b719-109">Return Value</span></span>  
 <span data-ttu-id="2b719-110">Wartość HRESULT, która wskazuje powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="2b719-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="2b719-111">Błędy można przetestować za pomocą makra nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="2b719-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b719-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b719-112">Requirements</span></span>  
 <span data-ttu-id="2b719-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b719-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b719-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2b719-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b719-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b719-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b719-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b719-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b719-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b719-117">See also</span></span>
- [<span data-ttu-id="2b719-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b719-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2b719-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b719-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
