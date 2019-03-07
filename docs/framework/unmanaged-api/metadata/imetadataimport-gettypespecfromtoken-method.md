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
ms.openlocfilehash: a8ecb529534f4ed1a1d12d9613ebd46f8b99fdb8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487513"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="d3c8c-102">IMetaDataImport::GetTypeSpecFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3c8c-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="d3c8c-103">Pobiera podpisu metadanych binarne specyfikacji typu reprezentowanego przez określony token.</span><span class="sxs-lookup"><span data-stu-id="d3c8c-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c8c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3c8c-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3c8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3c8c-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="d3c8c-106">[in] Token elementu TypeSpec związany z podpisem żądanego metadanych.</span><span class="sxs-lookup"><span data-stu-id="d3c8c-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="d3c8c-107">[out] Wskaźnik do podpisu metadanych binarnego.</span><span class="sxs-lookup"><span data-stu-id="d3c8c-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="d3c8c-108">[out] Rozmiar w bajtach podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d3c8c-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3c8c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3c8c-109">Return Value</span></span>  
 <span data-ttu-id="d3c8c-110">Wartość HRESULT, która wskazuje powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="d3c8c-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="d3c8c-111">Błędy można przetestować za pomocą makra nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d3c8c-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3c8c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3c8c-112">Requirements</span></span>  
 <span data-ttu-id="d3c8c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3c8c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3c8c-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d3c8c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3c8c-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3c8c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3c8c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3c8c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c8c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3c8c-117">See also</span></span>
- [<span data-ttu-id="d3c8c-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3c8c-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d3c8c-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3c8c-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
