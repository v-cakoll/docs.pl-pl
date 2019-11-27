---
title: IMetaDataError::OnError — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: f10c55abcc044b5bbdbb940001a25f530a4688e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431221"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="da9bc-102">IMetaDataError::OnError — Metoda</span><span class="sxs-lookup"><span data-stu-id="da9bc-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="da9bc-103">Zawiera powiadomienie o błędach występujących podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="da9bc-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da9bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da9bc-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da9bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da9bc-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="da9bc-106">podczas Wartość błędu HRESULT zwracana do metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="da9bc-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="da9bc-107">podczas Token metadanych obiektu kodu, który został scalony po wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="da9bc-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da9bc-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da9bc-108">Requirements</span></span>  
 <span data-ttu-id="da9bc-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da9bc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da9bc-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="da9bc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da9bc-111">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="da9bc-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da9bc-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da9bc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9bc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da9bc-113">See also</span></span>

- [<span data-ttu-id="da9bc-114">IMetaDataError, interfejs</span><span class="sxs-lookup"><span data-stu-id="da9bc-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
