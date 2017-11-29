---
title: "FreeWin32ResBlob — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.FreeWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: FreeWin32ResBlob
helpviewer_keywords: FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae7b01fee1460abfae8fc2f8f6c12a5f19d83b6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="33954-102">FreeWin32ResBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="33954-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="33954-103">Zwalnia blob zasobów Win32 i skojarzonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="33954-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33954-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33954-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33954-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33954-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="33954-106">Obiekt blob zasobów do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="33954-106">The resource blob to be released.</span></span> <span data-ttu-id="33954-107">Ta metoda przypisuje wskaźnika obiektu blob na wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="33954-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33954-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33954-108">Return Value</span></span>  
 <span data-ttu-id="33954-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="33954-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33954-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33954-110">Requirements</span></span>  
 <span data-ttu-id="33954-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="33954-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33954-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33954-112">See Also</span></span>  
 [<span data-ttu-id="33954-113">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="33954-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="33954-114">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="33954-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="33954-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="33954-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
