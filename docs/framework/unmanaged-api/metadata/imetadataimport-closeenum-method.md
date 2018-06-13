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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d81f9b0107fd927ddfda24cfd0ea3249e4c8651
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448820"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="3157e-102">IMetaDataImport::CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="3157e-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="3157e-103">Zamyka moduł wyliczający, który jest identyfikowany przez określone dojście.</span><span class="sxs-lookup"><span data-stu-id="3157e-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3157e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3157e-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3157e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3157e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3157e-106">[in] Dojście do modułu wyliczającego zamknąć.</span><span class="sxs-lookup"><span data-stu-id="3157e-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3157e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3157e-107">Remarks</span></span>  
 <span data-ttu-id="3157e-108">Dojście określone przez `hEnum` są uzyskiwane z poprzedniej `Enum` *nazwa* wywołania (na przykład [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="3157e-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3157e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3157e-109">Requirements</span></span>  
 <span data-ttu-id="3157e-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3157e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3157e-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3157e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3157e-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3157e-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3157e-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3157e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3157e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3157e-114">See Also</span></span>  
 [<span data-ttu-id="3157e-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3157e-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3157e-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3157e-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
