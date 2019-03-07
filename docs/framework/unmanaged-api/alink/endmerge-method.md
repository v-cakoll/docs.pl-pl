---
title: EndMerge — Metoda
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d4b102485db0199f748f6c5b6c4ab40d21429e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494418"
---
# <a name="endmerge-method"></a><span data-ttu-id="1d352-102">EndMerge — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d352-102">EndMerge Method</span></span>
<span data-ttu-id="1d352-103">Wskazuje, że wszystkie atrybuty niestandardowe zostały scalone w zakresie emitowanie.</span><span class="sxs-lookup"><span data-stu-id="1d352-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d352-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d352-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d352-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d352-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1d352-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d352-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d352-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d352-107">Return Value</span></span>  
 <span data-ttu-id="1d352-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1d352-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d352-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d352-109">Requirements</span></span>  
 <span data-ttu-id="1d352-110">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="1d352-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d352-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d352-111">See also</span></span>
- [<span data-ttu-id="1d352-112">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d352-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1d352-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d352-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1d352-114">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="1d352-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
