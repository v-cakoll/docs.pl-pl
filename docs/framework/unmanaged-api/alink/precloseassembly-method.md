---
title: "PreCloseAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.PreCloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: PreCloseAssembly
helpviewer_keywords: PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a4d1f2eed036552ab17b6768b7b2d84f4a52c9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="23d6d-102">PreCloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="23d6d-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="23d6d-103">Zamyka plik zestawu.</span><span class="sxs-lookup"><span data-stu-id="23d6d-103">Closes the assembly file.</span></span> <span data-ttu-id="23d6d-104">Tę metodę można wywołać po zamknięciu wszystkich innych plików, ale przed zamknięciem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="23d6d-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="23d6d-105">Nie wywołuj tej metody dla modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="23d6d-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d6d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="23d6d-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23d6d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="23d6d-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="23d6d-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="23d6d-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23d6d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="23d6d-109">Return Value</span></span>  
 <span data-ttu-id="23d6d-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="23d6d-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23d6d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23d6d-111">Requirements</span></span>  
 <span data-ttu-id="23d6d-112">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="23d6d-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d6d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23d6d-113">See Also</span></span>  
 [<span data-ttu-id="23d6d-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="23d6d-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="23d6d-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="23d6d-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="23d6d-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="23d6d-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
