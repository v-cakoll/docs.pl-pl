---
title: FreeWin32ResBlob — Metoda
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 196a57b3e919ea4ccbc0b91e5b6f281ad3c30b62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118160"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="7c2e9-102">FreeWin32ResBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c2e9-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="7c2e9-103">Zwalnia blob zasobów Win32 i skojarzonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c2e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c2e9-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c2e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c2e9-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="7c2e9-106">Obiekt blob zasobów mogą być wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-106">The resource blob to be released.</span></span> <span data-ttu-id="7c2e9-107">Ta metoda przypisuje wskaźnik obiektu blob na wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c2e9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7c2e9-108">Return Value</span></span>  
 <span data-ttu-id="7c2e9-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c2e9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c2e9-110">Requirements</span></span>  
 <span data-ttu-id="7c2e9-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="7c2e9-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2e9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c2e9-112">See also</span></span>

- [<span data-ttu-id="7c2e9-113">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7c2e9-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="7c2e9-114">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7c2e9-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="7c2e9-115">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="7c2e9-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
