---
title: IMetaDataImport::CountEnum — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c5e1cc3b47c6752017db19f7981a3810d19aca4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492143"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="80bae-102">IMetaDataImport::CountEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="80bae-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="80bae-103">Pobiera liczbę elementów w wyliczeniu, który został pobrany przez określony moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="80bae-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80bae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80bae-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80bae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80bae-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="80bae-106">[in] Dojście do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="80bae-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="80bae-107">[out] Liczba elementów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="80bae-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80bae-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80bae-108">Remarks</span></span>  
 <span data-ttu-id="80bae-109">Określone przez dojście `hEnum` są uzyskiwane z poprzedniego `Enum` *nazwa* wywołania (na przykład [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="80bae-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80bae-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80bae-110">Requirements</span></span>  
 <span data-ttu-id="80bae-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80bae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80bae-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="80bae-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80bae-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80bae-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80bae-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80bae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80bae-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80bae-115">See also</span></span>
- [<span data-ttu-id="80bae-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="80bae-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="80bae-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="80bae-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
