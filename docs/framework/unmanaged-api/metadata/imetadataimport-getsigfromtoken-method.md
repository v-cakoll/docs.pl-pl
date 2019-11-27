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
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="2ec87-102">IMetaDataImport::GetSigFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ec87-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="2ec87-103">Pobiera binarny podpis metadanych skojarzony z określonym tokenem.</span><span class="sxs-lookup"><span data-stu-id="2ec87-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ec87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ec87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ec87-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="2ec87-106">podczas Token, dla którego ma zostać zwrócona sygnatura metadanych binarnych.</span><span class="sxs-lookup"><span data-stu-id="2ec87-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="2ec87-107">określoną Wskaźnik do zwróconego podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2ec87-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="2ec87-108">określoną Rozmiar w bajtach binarnego podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2ec87-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec87-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ec87-109">Requirements</span></span>  
 <span data-ttu-id="2ec87-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ec87-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec87-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2ec87-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ec87-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2ec87-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ec87-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec87-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec87-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ec87-114">See also</span></span>

- [<span data-ttu-id="2ec87-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ec87-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2ec87-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ec87-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
