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
ms.openlocfilehash: 143b11f0a99081b7d49bfbb68b635d92cf1e9ba3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163881"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="41702-102">IMetaDataImport::ResetEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="41702-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="41702-103">Resetuje określonego modułu wyliczającego do określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="41702-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41702-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41702-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41702-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41702-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="41702-106">[in] Moduł wyliczający do zresetowania.</span><span class="sxs-lookup"><span data-stu-id="41702-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="41702-107">[in] Nowa pozycja, na którym ma zostać umieszczony moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="41702-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41702-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41702-108">Requirements</span></span>  
 <span data-ttu-id="41702-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41702-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41702-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="41702-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41702-111">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41702-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41702-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41702-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41702-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41702-113">See also</span></span>

- [<span data-ttu-id="41702-114">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="41702-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="41702-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="41702-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
