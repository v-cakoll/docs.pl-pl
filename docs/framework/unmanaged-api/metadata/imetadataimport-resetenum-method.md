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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777432"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="14bfa-102">IMetaDataImport::ResetEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="14bfa-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="14bfa-103">Resetuje określonego modułu wyliczającego do określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="14bfa-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14bfa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14bfa-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14bfa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14bfa-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="14bfa-106">[in] Moduł wyliczający do zresetowania.</span><span class="sxs-lookup"><span data-stu-id="14bfa-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="14bfa-107">[in] Nowa pozycja, na którym ma zostać umieszczony moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="14bfa-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14bfa-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14bfa-108">Requirements</span></span>  
 <span data-ttu-id="14bfa-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14bfa-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14bfa-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="14bfa-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14bfa-111">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14bfa-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14bfa-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14bfa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bfa-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14bfa-113">See also</span></span>

- [<span data-ttu-id="14bfa-114">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="14bfa-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="14bfa-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="14bfa-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
