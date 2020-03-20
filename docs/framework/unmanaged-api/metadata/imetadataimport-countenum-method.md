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
ms.openlocfilehash: b780ca513d8a0b4f88e66594e86e9ff8290f6523
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177364"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="a74b2-102">IMetaDataImport::CountEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="a74b2-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="a74b2-103">Pobiera liczbę elementów w wyliczenia, który został pobrany przez określonego wylicznika.</span><span class="sxs-lookup"><span data-stu-id="a74b2-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a74b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a74b2-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a74b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a74b2-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="a74b2-106">[w] Dojście do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="a74b2-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="a74b2-107">[na zewnątrz] Liczba wyliczonych elementów.</span><span class="sxs-lookup"><span data-stu-id="a74b2-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a74b2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a74b2-108">Remarks</span></span>  
 <span data-ttu-id="a74b2-109">Dojście `hEnum` określone przez jest `Enum`otrzymywany z poprzedniego *wywołania Name* (na przykład [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="a74b2-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a74b2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a74b2-110">Requirements</span></span>  
 <span data-ttu-id="a74b2-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a74b2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a74b2-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="a74b2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a74b2-113">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a74b2-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a74b2-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a74b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74b2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a74b2-115">See also</span></span>

- [<span data-ttu-id="a74b2-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a74b2-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a74b2-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a74b2-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
