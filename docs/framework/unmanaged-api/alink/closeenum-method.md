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
ms.openlocfilehash: 018af6929ad4023c70bfb975b9be010912415dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446564"
---
# <a name="closeenum-method"></a><span data-ttu-id="e01b3-102">CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="e01b3-102">CloseEnum Method</span></span>
<span data-ttu-id="e01b3-103">Closes the indicated enumeration and frees associated resources.</span><span class="sxs-lookup"><span data-stu-id="e01b3-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e01b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e01b3-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e01b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e01b3-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e01b3-106">Handle of enumeration to be closed.</span><span class="sxs-lookup"><span data-stu-id="e01b3-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e01b3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e01b3-107">Return Value</span></span>  
 <span data-ttu-id="e01b3-108">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="e01b3-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e01b3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e01b3-109">Requirements</span></span>  
 <span data-ttu-id="e01b3-110">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="e01b3-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01b3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e01b3-111">See also</span></span>

- [<span data-ttu-id="e01b3-112">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="e01b3-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e01b3-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e01b3-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e01b3-114">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="e01b3-114">ALink API</span></span>](index.md)
