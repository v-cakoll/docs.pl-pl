---
title: "EmitInternalExportedTypes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location: alink.dll
api_type: COM
f1_keywords: EmitInternalExportedTypes
helpviewer_keywords: EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f354058e0de944bbce9d128d3f4baa9b941fda08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="31ec6-102">EmitInternalExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="31ec6-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="31ec6-103">Emituje typy dodane do zestawu.</span><span class="sxs-lookup"><span data-stu-id="31ec6-103">Emits types added to the assembly.</span></span> <span data-ttu-id="31ec6-104">Wywołać tę metodę po wiadomo, że dodano wewnętrzne typy.</span><span class="sxs-lookup"><span data-stu-id="31ec6-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31ec6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="31ec6-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31ec6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="31ec6-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="31ec6-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="31ec6-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31ec6-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="31ec6-108">Return Value</span></span>  
 <span data-ttu-id="31ec6-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="31ec6-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ec6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31ec6-110">Requirements</span></span>  
 <span data-ttu-id="31ec6-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="31ec6-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ec6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31ec6-112">See Also</span></span>  
 [<span data-ttu-id="31ec6-113">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="31ec6-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="31ec6-114">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="31ec6-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="31ec6-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="31ec6-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
