---
title: "IAssemblyCacheItem — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCacheItem
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCacheItem
helpviewer_keywords: IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 323b501efbdf309d5e0d595137407dd8289de17a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="9dc7f-102">IAssemblyCacheItem — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9dc7f-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="9dc7f-103">Reprezentuje pojedynczy zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="9dc7f-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9dc7f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9dc7f-104">Methods</span></span>  
  
|<span data-ttu-id="9dc7f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9dc7f-105">Method</span></span>|<span data-ttu-id="9dc7f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9dc7f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9dc7f-107">AbortItem, metoda</span><span class="sxs-lookup"><span data-stu-id="9dc7f-107">AbortItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="9dc7f-108">Umożliwia zestawu w globalnej pamięci podręcznej zestawów do wykonywania operacji oczyszczania przed jego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="9dc7f-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="9dc7f-109">Commit, metoda</span><span class="sxs-lookup"><span data-stu-id="9dc7f-109">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|<span data-ttu-id="9dc7f-110">Zatwierdza odwołanie do zestawu pamięci podręcznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="9dc7f-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="9dc7f-111">CreateStream, metoda</span><span class="sxs-lookup"><span data-stu-id="9dc7f-111">CreateStream Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|<span data-ttu-id="9dc7f-112">Tworzy strumień o określonej nazwie i format.</span><span class="sxs-lookup"><span data-stu-id="9dc7f-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9dc7f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9dc7f-113">Requirements</span></span>  
 <span data-ttu-id="9dc7f-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc7f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc7f-115">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9dc7f-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9dc7f-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc7f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc7f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dc7f-117">See Also</span></span>  
 [<span data-ttu-id="9dc7f-118">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="9dc7f-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="9dc7f-119">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="9dc7f-119">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="9dc7f-120">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="9dc7f-120">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
