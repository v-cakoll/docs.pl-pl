---
title: IMetaDataEmit::SetFieldRVA — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ebde1d506a120a99e1c637c660b45d698994f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992475"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="5e95f-102">IMetaDataEmit::SetFieldRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e95f-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="5e95f-103">Ustawia wartość zmiennej globalnej dla względne wirtualnego adresu pola przywoływane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="5e95f-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e95f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e95f-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e95f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e95f-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="5e95f-106">[in] Token do pola docelowego.</span><span class="sxs-lookup"><span data-stu-id="5e95f-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="5e95f-107">[in] Adres obszaru kodu lub danych.</span><span class="sxs-lookup"><span data-stu-id="5e95f-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e95f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e95f-108">Requirements</span></span>  
 <span data-ttu-id="5e95f-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e95f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e95f-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5e95f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e95f-111">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e95f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e95f-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e95f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e95f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e95f-113">See also</span></span>

- [<span data-ttu-id="5e95f-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e95f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5e95f-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e95f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
