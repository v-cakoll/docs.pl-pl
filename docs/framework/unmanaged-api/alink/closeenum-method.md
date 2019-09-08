---
title: CloseEnum — Metoda
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d9529022eb04c81152dced5c63f255c510851a0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777475"
---
# <a name="closeenum-method"></a><span data-ttu-id="1c65c-102">CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c65c-102">CloseEnum Method</span></span>
<span data-ttu-id="1c65c-103">Zamyka wskazane Wyliczenie i zwalnia skojarzone zasoby.</span><span class="sxs-lookup"><span data-stu-id="1c65c-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c65c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c65c-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c65c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c65c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="1c65c-106">Dojście wyliczenia do zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1c65c-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c65c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c65c-107">Return Value</span></span>  
 <span data-ttu-id="1c65c-108">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1c65c-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c65c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c65c-109">Requirements</span></span>  
 <span data-ttu-id="1c65c-110">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="1c65c-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c65c-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c65c-111">See also</span></span>

- [<span data-ttu-id="1c65c-112">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c65c-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1c65c-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c65c-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1c65c-114">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="1c65c-114">ALink API</span></span>](index.md)
