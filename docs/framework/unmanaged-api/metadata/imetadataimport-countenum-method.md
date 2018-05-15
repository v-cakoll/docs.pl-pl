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
ms.openlocfilehash: a8e30020a8296e037d1dacc8dbaabde7e40032e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="410c2-102">IMetaDataImport::CountEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="410c2-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="410c2-103">Pobiera liczbę elementów w wyliczeniu została pobrana przez określony moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="410c2-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="410c2-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="410c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="410c2-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="410c2-106">[in] Dojście do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="410c2-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="410c2-107">[out] Liczba elementów wyliczone.</span><span class="sxs-lookup"><span data-stu-id="410c2-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="410c2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="410c2-108">Remarks</span></span>  
 <span data-ttu-id="410c2-109">Dojście określone przez `hEnum` są uzyskiwane z poprzedniej `Enum` *nazwa* wywołania (na przykład [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="410c2-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="410c2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="410c2-110">Requirements</span></span>  
 <span data-ttu-id="410c2-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="410c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410c2-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="410c2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="410c2-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="410c2-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="410c2-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="410c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410c2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="410c2-115">See Also</span></span>  
 [<span data-ttu-id="410c2-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="410c2-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="410c2-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="410c2-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
