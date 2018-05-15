---
title: CALL_ID — Struktura
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8d6b16f3eeb32e41f3568e0b237f18c945a8cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="callid-structure"></a><span data-ttu-id="f7a21-102">CALL_ID — Struktura</span><span class="sxs-lookup"><span data-stu-id="f7a21-102">CALL_ID Structure</span></span>
<span data-ttu-id="f7a21-103">Zapewnia informacje o debugera o funkcję, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f7a21-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="f7a21-104">Zobacz [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interfejsu, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f7a21-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a21-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7a21-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f7a21-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f7a21-106">Members</span></span>  
  
|<span data-ttu-id="f7a21-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f7a21-107">Member</span></span>|<span data-ttu-id="f7a21-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f7a21-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="f7a21-109">Identyfikuje komputer, który jest wywołania.</span><span class="sxs-lookup"><span data-stu-id="f7a21-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="f7a21-110">Identyfikuje procesora komputera.</span><span class="sxs-lookup"><span data-stu-id="f7a21-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="f7a21-111">Identyfikuje wątku, który wykonuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f7a21-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="f7a21-112">Określa adres stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="f7a21-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="f7a21-113">Określa adres wywołania.</span><span class="sxs-lookup"><span data-stu-id="f7a21-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="f7a21-114">Identyfikuje komputer, który będzie wykonywać wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f7a21-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7a21-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7a21-115">Requirements</span></span>  
 <span data-ttu-id="f7a21-116">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="f7a21-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a21-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7a21-117">See Also</span></span>  
 [<span data-ttu-id="f7a21-118">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7a21-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="f7a21-119">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="f7a21-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
