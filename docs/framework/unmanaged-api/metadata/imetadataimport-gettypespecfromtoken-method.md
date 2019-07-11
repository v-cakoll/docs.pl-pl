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
ms.openlocfilehash: e7e060d2f72609b470dbd5060746a1458f5eed9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782311"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="5a26e-102">IMetaDataImport::GetTypeSpecFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a26e-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="5a26e-103">Pobiera podpisu metadanych binarne specyfikacji typu reprezentowanego przez określony token.</span><span class="sxs-lookup"><span data-stu-id="5a26e-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a26e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a26e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a26e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a26e-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="5a26e-106">[in] Token elementu TypeSpec związany z podpisem żądanego metadanych.</span><span class="sxs-lookup"><span data-stu-id="5a26e-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="5a26e-107">[out] Wskaźnik do podpisu metadanych binarnego.</span><span class="sxs-lookup"><span data-stu-id="5a26e-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="5a26e-108">[out] Rozmiar w bajtach podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="5a26e-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a26e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5a26e-109">Return Value</span></span>  
 <span data-ttu-id="5a26e-110">Wartość HRESULT, która wskazuje powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="5a26e-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="5a26e-111">Błędy można przetestować za pomocą makra nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="5a26e-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a26e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a26e-112">Requirements</span></span>  
 <span data-ttu-id="5a26e-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a26e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a26e-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5a26e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a26e-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a26e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a26e-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a26e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a26e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a26e-117">See also</span></span>

- [<span data-ttu-id="5a26e-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a26e-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5a26e-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a26e-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
