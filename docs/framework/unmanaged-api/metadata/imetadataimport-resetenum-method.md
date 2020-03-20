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
ms.openlocfilehash: 3dd82588cf2dbf92fdda66fd7674c17ddc8b7306
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177188"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="e9879-102">IMetaDataImport::ResetEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9879-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="e9879-103">Resetuje określony wyliczacz do określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="e9879-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9879-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9879-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9879-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9879-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e9879-106">[w] Wyliczacz do zresetowania.</span><span class="sxs-lookup"><span data-stu-id="e9879-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="e9879-107">[w] Nowa pozycja, w której ma być umieszczany wyliczacz.</span><span class="sxs-lookup"><span data-stu-id="e9879-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9879-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9879-108">Requirements</span></span>  
 <span data-ttu-id="e9879-109">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9879-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9879-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="e9879-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9879-111">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9879-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9879-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9879-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9879-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9879-113">See also</span></span>

- [<span data-ttu-id="e9879-114">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e9879-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e9879-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9879-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
