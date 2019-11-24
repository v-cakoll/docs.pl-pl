---
title: IMetaDataImport::CloseEnum — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: 4347a4da3e58a20c98e217de3a71c448e244eb29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440121"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="3f7bd-102">IMetaDataImport::CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f7bd-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="3f7bd-103">Closes the enumerator that is identified by the specified handle.</span><span class="sxs-lookup"><span data-stu-id="3f7bd-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f7bd-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f7bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f7bd-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3f7bd-106">[in] The handle for the enumerator to close.</span><span class="sxs-lookup"><span data-stu-id="3f7bd-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f7bd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f7bd-107">Remarks</span></span>  
 <span data-ttu-id="3f7bd-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="3f7bd-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7bd-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f7bd-109">Requirements</span></span>  
 <span data-ttu-id="3f7bd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f7bd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f7bd-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f7bd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f7bd-112">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f7bd-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f7bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f7bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7bd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f7bd-114">See also</span></span>

- [<span data-ttu-id="3f7bd-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3f7bd-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3f7bd-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3f7bd-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
