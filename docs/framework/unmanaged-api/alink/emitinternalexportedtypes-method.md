---
title: "EmitInternalExportedTypes — Metoda"
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
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48ad5e34b926cf3dab562f57bb9206fa0ba70e6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="9cfd8-102">EmitInternalExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cfd8-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="9cfd8-103">Emituje typy dodane do zestawu.</span><span class="sxs-lookup"><span data-stu-id="9cfd8-103">Emits types added to the assembly.</span></span> <span data-ttu-id="9cfd8-104">Wywołać tę metodę po wiadomo, że dodano wewnętrzne typy.</span><span class="sxs-lookup"><span data-stu-id="9cfd8-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cfd8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cfd8-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cfd8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cfd8-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9cfd8-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="9cfd8-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cfd8-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9cfd8-108">Return Value</span></span>  
 <span data-ttu-id="9cfd8-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9cfd8-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cfd8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cfd8-110">Requirements</span></span>  
 <span data-ttu-id="9cfd8-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="9cfd8-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfd8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cfd8-112">See Also</span></span>  
 [<span data-ttu-id="9cfd8-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cfd8-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9cfd8-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cfd8-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9cfd8-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="9cfd8-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
