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
ms.openlocfilehash: 0c78ce8192d6456dd1b1be990d87b9209b028e09
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440359"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="6d29a-102">IMetaDataImport::CountEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d29a-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="6d29a-103">Pobiera liczbę elementów w wyliczeniu, która została pobrana przez określony moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="6d29a-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d29a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d29a-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d29a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d29a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="6d29a-106">podczas Uchwyt dla modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="6d29a-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="6d29a-107">określoną Liczba wyliczonych elementów.</span><span class="sxs-lookup"><span data-stu-id="6d29a-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d29a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d29a-108">Remarks</span></span>  
 <span data-ttu-id="6d29a-109">Dojście określone przez `hEnum` jest uzyskiwane z poprzedniego wywołania *nazwy* `Enum`(na przykład [IMetaDataImport:: EnumTypeDefs —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="6d29a-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d29a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d29a-110">Requirements</span></span>  
 <span data-ttu-id="6d29a-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d29a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d29a-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6d29a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d29a-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6d29a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d29a-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d29a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d29a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d29a-115">See also</span></span>

- [<span data-ttu-id="6d29a-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d29a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6d29a-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d29a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
