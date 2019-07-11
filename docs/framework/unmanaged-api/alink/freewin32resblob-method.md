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
ms.openlocfilehash: 75aec187452e2f9f442a5d4856fe6777c03f34c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741980"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="0d462-102">FreeWin32ResBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d462-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="0d462-103">Zwalnia blob zasobów Win32 i skojarzonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="0d462-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d462-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d462-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d462-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d462-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="0d462-106">Obiekt blob zasobów mogą być wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="0d462-106">The resource blob to be released.</span></span> <span data-ttu-id="0d462-107">Ta metoda przypisuje wskaźnik obiektu blob na wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="0d462-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d462-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0d462-108">Return Value</span></span>  
 <span data-ttu-id="0d462-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0d462-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d462-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d462-110">Requirements</span></span>  
 <span data-ttu-id="0d462-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="0d462-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d462-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d462-112">See also</span></span>

- [<span data-ttu-id="0d462-113">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d462-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0d462-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d462-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0d462-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="0d462-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
