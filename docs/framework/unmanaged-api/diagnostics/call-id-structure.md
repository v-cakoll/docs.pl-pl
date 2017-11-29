---
title: "CALL_ID — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CALL_ID
api_location: diasymreader.dll
api_type: COM
f1_keywords: CALL_ID
helpviewer_keywords: CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c44db9021a7dbf5b497db3536eddcea020e71bf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="callid-structure"></a><span data-ttu-id="22c10-102">CALL_ID — Struktura</span><span class="sxs-lookup"><span data-stu-id="22c10-102">CALL_ID Structure</span></span>
<span data-ttu-id="22c10-103">Zapewnia informacje o debugera o funkcję, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="22c10-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="22c10-104">Zobacz [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interfejsu, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="22c10-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c10-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="22c10-105">Syntax</span></span>  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="22c10-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="22c10-106">Members</span></span>  
  
|<span data-ttu-id="22c10-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="22c10-107">Member</span></span>|<span data-ttu-id="22c10-108">Opis</span><span class="sxs-lookup"><span data-stu-id="22c10-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="22c10-109">Identyfikuje komputer, który jest wywołania.</span><span class="sxs-lookup"><span data-stu-id="22c10-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="22c10-110">Identyfikuje procesora komputera.</span><span class="sxs-lookup"><span data-stu-id="22c10-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="22c10-111">Identyfikuje wątku, który wykonuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="22c10-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="22c10-112">Określa adres stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="22c10-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="22c10-113">Określa adres wywołania.</span><span class="sxs-lookup"><span data-stu-id="22c10-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="22c10-114">Identyfikuje komputer, który będzie wykonywać wywołanie.</span><span class="sxs-lookup"><span data-stu-id="22c10-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22c10-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22c10-115">Requirements</span></span>  
 <span data-ttu-id="22c10-116">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="22c10-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c10-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22c10-117">See Also</span></span>  
 [<span data-ttu-id="22c10-118">INotifySink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="22c10-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="22c10-119">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="22c10-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
