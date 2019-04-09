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
ms.openlocfilehash: fd7d63596690e2a5d0bc26448884ec09ecd63231
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129522"
---
# <a name="closeenum-method"></a><span data-ttu-id="bf002-102">CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf002-102">CloseEnum Method</span></span>
<span data-ttu-id="bf002-103">Zamyka wskazany wyliczenie i zwalnia skojarzonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="bf002-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf002-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf002-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf002-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf002-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="bf002-106">Dojście do wyliczenia zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="bf002-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf002-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bf002-107">Return Value</span></span>  
 <span data-ttu-id="bf002-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="bf002-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf002-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf002-109">Requirements</span></span>  
 <span data-ttu-id="bf002-110">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="bf002-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf002-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf002-111">See also</span></span>

- [<span data-ttu-id="bf002-112">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bf002-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="bf002-113">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bf002-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="bf002-114">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="bf002-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
