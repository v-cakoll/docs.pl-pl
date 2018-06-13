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
ms.openlocfilehash: e8f9eecd6d6d74717eb7c1e389bfa24e40afc950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402577"
---
# <a name="endmerge-method"></a><span data-ttu-id="71b47-102">EndMerge — Metoda</span><span class="sxs-lookup"><span data-stu-id="71b47-102">EndMerge Method</span></span>
<span data-ttu-id="71b47-103">Wskazuje, że wszystkie atrybuty niestandardowe zostały scalone w zakresie emitowanie.</span><span class="sxs-lookup"><span data-stu-id="71b47-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71b47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71b47-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71b47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71b47-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="71b47-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="71b47-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71b47-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="71b47-107">Return Value</span></span>  
 <span data-ttu-id="71b47-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="71b47-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71b47-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71b47-109">Requirements</span></span>  
 <span data-ttu-id="71b47-110">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="71b47-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b47-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71b47-111">See Also</span></span>  
 [<span data-ttu-id="71b47-112">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="71b47-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="71b47-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="71b47-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="71b47-114">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="71b47-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
