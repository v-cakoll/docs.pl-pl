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
ms.openlocfilehash: 7f27955467436d562c6a9acc9d7f666427e4c85b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770714"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="d1242-102">IMetaDataImport::CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1242-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="d1242-103">Zamyka moduł wyliczający, który jest identyfikowany przez określone dojście.</span><span class="sxs-lookup"><span data-stu-id="d1242-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1242-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1242-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1242-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1242-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="d1242-106">[in] Dojście dla typu wyliczeniowego zamknąć.</span><span class="sxs-lookup"><span data-stu-id="d1242-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1242-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1242-107">Remarks</span></span>  
 <span data-ttu-id="d1242-108">Określone przez dojście `hEnum` są uzyskiwane z poprzedniego `Enum` *nazwa* wywołania (na przykład [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="d1242-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1242-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1242-109">Requirements</span></span>  
 <span data-ttu-id="d1242-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1242-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1242-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d1242-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1242-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1242-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1242-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1242-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1242-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1242-114">See also</span></span>

- [<span data-ttu-id="d1242-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1242-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d1242-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1242-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
