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
ms.openlocfilehash: 54c35f4f7a7f933bbc06a641d9ba00c5059b5ff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="032c5-102">IMetaDataImport::GetTypeSpecFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="032c5-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="032c5-103">Pobiera podpisu metadanych binarne specyfikacji typu reprezentowanego przez określony token.</span><span class="sxs-lookup"><span data-stu-id="032c5-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="032c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="032c5-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="032c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="032c5-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="032c5-106">[in] Token elementu TypeSpec skojarzony z sygnaturą żądanych metadanych.</span><span class="sxs-lookup"><span data-stu-id="032c5-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="032c5-107">[out] Wskaźnik do podpisu metadanych binarnego.</span><span class="sxs-lookup"><span data-stu-id="032c5-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="032c5-108">[out] Rozmiar w bajtach podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="032c5-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="032c5-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="032c5-109">Return Value</span></span>  
 <span data-ttu-id="032c5-110">HRESULT, która wskazuje powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="032c5-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="032c5-111">Błędy można przetestować z makro nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="032c5-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="032c5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="032c5-112">Requirements</span></span>  
 <span data-ttu-id="032c5-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="032c5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="032c5-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="032c5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="032c5-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="032c5-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="032c5-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="032c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032c5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="032c5-117">See Also</span></span>  
 [<span data-ttu-id="032c5-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="032c5-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="032c5-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="032c5-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
