---
title: USER_THREAD — Struktura
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acc4da79796e975d349d1cb33c301c25c4791cb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709081"
---
# <a name="userthread-structure"></a><span data-ttu-id="ff9a7-102">USER_THREAD — Struktura</span><span class="sxs-lookup"><span data-stu-id="ff9a7-102">USER_THREAD Structure</span></span>
<span data-ttu-id="ff9a7-103">Informacje o wątku debugera.</span><span class="sxs-lookup"><span data-stu-id="ff9a7-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="ff9a7-104">Aby uzyskać więcej informacji, zobacz [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ff9a7-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9a7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff9a7-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="ff9a7-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ff9a7-106">Members</span></span>  
  
|<span data-ttu-id="ff9a7-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ff9a7-107">Member</span></span>|<span data-ttu-id="ff9a7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ff9a7-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="ff9a7-109">Adres buforu wątku.</span><span class="sxs-lookup"><span data-stu-id="ff9a7-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="ff9a7-110">Długość buforu wątku, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ff9a7-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="ff9a7-111">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="ff9a7-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff9a7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff9a7-112">Requirements</span></span>  
 <span data-ttu-id="ff9a7-113">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="ff9a7-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9a7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff9a7-114">See also</span></span>
- [<span data-ttu-id="ff9a7-115">SetNotifyFilter, metoda</span><span class="sxs-lookup"><span data-stu-id="ff9a7-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="ff9a7-116">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="ff9a7-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
