---
title: IMetaDataImport::ResetEnum — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56fc0273fb2c1b77c74d7a1d853886f47170497e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447931"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="3bafc-102">IMetaDataImport::ResetEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="3bafc-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="3bafc-103">Resetuje określonego modułu wyliczającego do określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="3bafc-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bafc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bafc-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bafc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bafc-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3bafc-106">[in] Moduł wyliczający, aby zresetować.</span><span class="sxs-lookup"><span data-stu-id="3bafc-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="3bafc-107">[in] Nowa pozycja w której ma zostać umieszczony element wyliczający.</span><span class="sxs-lookup"><span data-stu-id="3bafc-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bafc-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bafc-108">Requirements</span></span>  
 <span data-ttu-id="3bafc-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bafc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bafc-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3bafc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3bafc-111">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3bafc-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3bafc-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bafc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bafc-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bafc-113">See Also</span></span>  
 [<span data-ttu-id="3bafc-114">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3bafc-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3bafc-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3bafc-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
