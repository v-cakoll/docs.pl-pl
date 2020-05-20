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
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609446"
---
# <a name="user_thread-structure"></a><span data-ttu-id="3b5d7-102">USER_THREAD — Struktura</span><span class="sxs-lookup"><span data-stu-id="3b5d7-102">USER_THREAD Structure</span></span>
<span data-ttu-id="3b5d7-103">Zawiera informacje dotyczące debugera wątku.</span><span class="sxs-lookup"><span data-stu-id="3b5d7-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="3b5d7-104">Aby uzyskać więcej informacji, zobacz metodę [INotifySource2:: SetNotifyFilter —](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3b5d7-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5d7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b5d7-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="3b5d7-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3b5d7-106">Members</span></span>  
  
|<span data-ttu-id="3b5d7-107">Członek</span><span class="sxs-lookup"><span data-stu-id="3b5d7-107">Member</span></span>|<span data-ttu-id="3b5d7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3b5d7-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="3b5d7-109">Adres buforu wątku.</span><span class="sxs-lookup"><span data-stu-id="3b5d7-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="3b5d7-110">Długość buforu wątku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="3b5d7-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="3b5d7-111">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="3b5d7-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b5d7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b5d7-112">Requirements</span></span>  
 <span data-ttu-id="3b5d7-113">**Nagłówek:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="3b5d7-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5d7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b5d7-114">See also</span></span>

- [<span data-ttu-id="3b5d7-115">SetNotifyFilter, metoda</span><span class="sxs-lookup"><span data-stu-id="3b5d7-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="3b5d7-116">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="3b5d7-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
