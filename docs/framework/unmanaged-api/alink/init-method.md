---
title: "Init — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.Init
api_location: alink.dll
api_type: COM
f1_keywords: Init
helpviewer_keywords: Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 999f572d27f75094ecc72c59acee7d35f86d5342
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="init-method"></a><span data-ttu-id="c5aa3-102">Init — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5aa3-102">Init Method</span></span>
<span data-ttu-id="c5aa3-103">Przygotowuje obiektów implementacja [ialink — interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) do użycia.</span><span class="sxs-lookup"><span data-stu-id="c5aa3-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5aa3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5aa3-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5aa3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5aa3-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="c5aa3-106">[IMetaDataDispenserEx — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) wskaźnik do rozdzielacz metadanych.</span><span class="sxs-lookup"><span data-stu-id="c5aa3-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="c5aa3-107">[IMetaDataError — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) wskaźnik do obsługi interfejsu opcjonalne błędów.</span><span class="sxs-lookup"><span data-stu-id="c5aa3-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5aa3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c5aa3-108">Return Value</span></span>  
 <span data-ttu-id="c5aa3-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c5aa3-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5aa3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5aa3-110">Requirements</span></span>  
 <span data-ttu-id="c5aa3-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="c5aa3-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5aa3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5aa3-112">See Also</span></span>  
 [<span data-ttu-id="c5aa3-113">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="c5aa3-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c5aa3-114">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="c5aa3-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c5aa3-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="c5aa3-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
