---
title: IMetaDataEmit::GetTokenFromSig — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
ms.openlocfilehash: f1262181fa745e1b6d3fc48a4ad728c1020705b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434315"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="9052c-102">IMetaDataEmit::GetTokenFromSig — Metoda</span><span class="sxs-lookup"><span data-stu-id="9052c-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="9052c-103">Pobiera token dla określonej sygnatury metadanych.</span><span class="sxs-lookup"><span data-stu-id="9052c-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9052c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9052c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9052c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9052c-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="9052c-106">podczas Podpis, który ma zostać utrwalony i zapisany.</span><span class="sxs-lookup"><span data-stu-id="9052c-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="9052c-107">podczas Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="9052c-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="9052c-108">określoną Przypisany token `mdSignature`.</span><span class="sxs-lookup"><span data-stu-id="9052c-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9052c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9052c-109">Requirements</span></span>  
 <span data-ttu-id="9052c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9052c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9052c-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9052c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9052c-112">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9052c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9052c-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9052c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9052c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9052c-114">See also</span></span>

- [<span data-ttu-id="9052c-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="9052c-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9052c-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9052c-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
