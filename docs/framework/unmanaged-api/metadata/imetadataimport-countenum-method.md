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
ms.openlocfilehash: 4521a3f15ec358a4d786a4533efb6b99d0e1c1cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492385"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="461a3-102">IMetaDataImport::CountEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="461a3-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="461a3-103">Pobiera liczbę elementów w wyliczeniu, która została pobrana przez określony moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="461a3-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="461a3-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="461a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="461a3-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="461a3-106">podczas Uchwyt dla modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="461a3-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="461a3-107">określoną Liczba wyliczonych elementów.</span><span class="sxs-lookup"><span data-stu-id="461a3-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="461a3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="461a3-108">Remarks</span></span>  
 <span data-ttu-id="461a3-109">Dojście określone przez `hEnum` jest uzyskiwane z poprzedniego `Enum` wywołania *nazwy* (na przykład [IMetaDataImport:: EnumTypeDefs —](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="461a3-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="461a3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="461a3-110">Requirements</span></span>  
 <span data-ttu-id="461a3-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="461a3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="461a3-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="461a3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="461a3-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="461a3-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="461a3-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461a3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="461a3-115">See also</span></span>

- [<span data-ttu-id="461a3-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="461a3-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="461a3-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="461a3-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
