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
ms.openlocfilehash: 7846eeceeb4d59c4e9aae73c79172c89184396e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123872"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="7355b-102">IMetaDataImport::CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="7355b-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="7355b-103">Zamyka moduł wyliczający, który jest identyfikowany przez określone dojście.</span><span class="sxs-lookup"><span data-stu-id="7355b-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7355b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7355b-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7355b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7355b-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="7355b-106">[in] Dojście dla typu wyliczeniowego zamknąć.</span><span class="sxs-lookup"><span data-stu-id="7355b-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7355b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7355b-107">Remarks</span></span>  
 <span data-ttu-id="7355b-108">Określone przez dojście `hEnum` są uzyskiwane z poprzedniego `Enum` *nazwa* wywołania (na przykład [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="7355b-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7355b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7355b-109">Requirements</span></span>  
 <span data-ttu-id="7355b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7355b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7355b-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7355b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7355b-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7355b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7355b-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7355b-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7355b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7355b-114">See also</span></span>

- [<span data-ttu-id="7355b-115">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7355b-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7355b-116">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7355b-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
