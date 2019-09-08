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
ms.openlocfilehash: ea0fbceb1e778a2f26e0625a337b803f417b59eb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777247"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="01d97-102">FreeWin32ResBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="01d97-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="01d97-103">Zwalnia obiekt BLOB zasobów Win32 i skojarzone zasoby.</span><span class="sxs-lookup"><span data-stu-id="01d97-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01d97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01d97-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="01d97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01d97-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="01d97-106">Obiekt BLOB zasobu do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="01d97-106">The resource blob to be released.</span></span> <span data-ttu-id="01d97-107">Ta metoda przypisuje wskaźnik obiektu BLOB do wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="01d97-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01d97-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="01d97-108">Return Value</span></span>  
 <span data-ttu-id="01d97-109">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="01d97-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01d97-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01d97-110">Requirements</span></span>  
 <span data-ttu-id="01d97-111">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="01d97-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d97-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01d97-112">See also</span></span>

- [<span data-ttu-id="01d97-113">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="01d97-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="01d97-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="01d97-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="01d97-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="01d97-115">ALink API</span></span>](index.md)
