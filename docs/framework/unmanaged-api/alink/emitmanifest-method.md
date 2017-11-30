---
title: "EmitManifest — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitManifest
- IALink.EmitManifest
api_location: alink.dll
api_type: COM
f1_keywords: EmitManifest
helpviewer_keywords: EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03ef815f03a65cbf7e2dc936b21848e206132add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="emitmanifest-method"></a><span data-ttu-id="dd831-102">EmitManifest — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd831-102">EmitManifest Method</span></span>
<span data-ttu-id="dd831-103">Emituje końcowego manifestu.</span><span class="sxs-lookup"><span data-stu-id="dd831-103">Emits the final manifest.</span></span> <span data-ttu-id="dd831-104">Tę metodę można wywołać po zaimportowaniu wszystkie inne pliki i ustawieniu wszystkich opcji.</span><span class="sxs-lookup"><span data-stu-id="dd831-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="dd831-105">Nie wywołuj tej metody dla modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="dd831-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd831-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd831-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd831-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd831-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="dd831-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="dd831-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="dd831-109">Odbiera rozmiar do zarezerwowania w pliku zestawu pobierane z [StrongNameSignatureSize — funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="dd831-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="dd831-110">Opcjonalnie otrzymuje token manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="dd831-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd831-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd831-111">Return Value</span></span>  
 <span data-ttu-id="dd831-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="dd831-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd831-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd831-113">Requirements</span></span>  
 <span data-ttu-id="dd831-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="dd831-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd831-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd831-115">See Also</span></span>  
 [<span data-ttu-id="dd831-116">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="dd831-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="dd831-117">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="dd831-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="dd831-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="dd831-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
