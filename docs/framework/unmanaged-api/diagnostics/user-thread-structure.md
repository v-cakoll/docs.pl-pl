---
title: "USER_THREAD — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: USER_THREAD
api_location: diasymreader.dll
api_type: COM
f1_keywords: USER_THREAD
helpviewer_keywords: USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 50533ce25812ad49d538c5a6a6c814d7a9704053
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="userthread-structure"></a><span data-ttu-id="ae1bb-102">USER_THREAD — Struktura</span><span class="sxs-lookup"><span data-stu-id="ae1bb-102">USER_THREAD Structure</span></span>
<span data-ttu-id="ae1bb-103">Zapewnia informacje o debugerze o wątku.</span><span class="sxs-lookup"><span data-stu-id="ae1bb-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="ae1bb-104">Aby uzyskać więcej informacji, zobacz [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ae1bb-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae1bb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae1bb-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="ae1bb-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ae1bb-106">Members</span></span>  
  
|<span data-ttu-id="ae1bb-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ae1bb-107">Member</span></span>|<span data-ttu-id="ae1bb-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ae1bb-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="ae1bb-109">Adres buforu wątku.</span><span class="sxs-lookup"><span data-stu-id="ae1bb-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="ae1bb-110">Długość buforu wątku, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ae1bb-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="ae1bb-111">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="ae1bb-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae1bb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae1bb-112">Requirements</span></span>  
 <span data-ttu-id="ae1bb-113">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="ae1bb-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1bb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae1bb-114">See Also</span></span>  
 [<span data-ttu-id="ae1bb-115">SetNotifyFilter, metoda</span><span class="sxs-lookup"><span data-stu-id="ae1bb-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="ae1bb-116">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="ae1bb-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
