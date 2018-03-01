---
title: "EmitAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f012ea89fec0e64bc1639e6c47fb79249c25411a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="1ccf9-102">EmitAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ccf9-102">EmitAssembly Method</span></span>
<span data-ttu-id="1ccf9-103">Tworzy zestaw.</span><span class="sxs-lookup"><span data-stu-id="1ccf9-103">Creates the assembly.</span></span> <span data-ttu-id="1ccf9-104">Tę metodę można wywołać po zamknięciu wszystkich innych plików z wyjątkiem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="1ccf9-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="1ccf9-105">Ta metoda zostanie wywołana podczas produkowania niezwiązanego modułów.</span><span class="sxs-lookup"><span data-stu-id="1ccf9-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ccf9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ccf9-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ccf9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ccf9-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1ccf9-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="1ccf9-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ccf9-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1ccf9-109">Return Value</span></span>  
 <span data-ttu-id="1ccf9-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1ccf9-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ccf9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ccf9-111">Requirements</span></span>  
 <span data-ttu-id="1ccf9-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="1ccf9-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ccf9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ccf9-113">See Also</span></span>  
 [<span data-ttu-id="1ccf9-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ccf9-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1ccf9-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ccf9-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1ccf9-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="1ccf9-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
