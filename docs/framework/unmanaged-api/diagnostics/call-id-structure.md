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
ms.openlocfilehash: 1c795ee536483a7def9c0339efae66a013898a77
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420633"
---
# <a name="call_id-structure"></a><span data-ttu-id="9041c-102">CALL_ID — Struktura</span><span class="sxs-lookup"><span data-stu-id="9041c-102">CALL_ID Structure</span></span>
<span data-ttu-id="9041c-103">Dostarcza informacje do debugera dotyczące funkcji, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9041c-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="9041c-104">Aby uzyskać więcej informacji, zobacz Interfejs [INotifySink2](inotifysink2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9041c-104">See the [INotifySink2](inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9041c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9041c-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="9041c-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9041c-106">Members</span></span>  
  
|<span data-ttu-id="9041c-107">Członek</span><span class="sxs-lookup"><span data-stu-id="9041c-107">Member</span></span>|<span data-ttu-id="9041c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9041c-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="9041c-109">Identyfikuje maszynę, która wywołuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="9041c-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="9041c-110">Identyfikuje procesor maszyny.</span><span class="sxs-lookup"><span data-stu-id="9041c-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="9041c-111">Identyfikuje wątek wykonujący wywołanie.</span><span class="sxs-lookup"><span data-stu-id="9041c-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="9041c-112">Określa adres stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="9041c-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="9041c-113">Określa adres wywołania.</span><span class="sxs-lookup"><span data-stu-id="9041c-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="9041c-114">Identyfikuje maszynę, która będzie wykonywać wywołanie.</span><span class="sxs-lookup"><span data-stu-id="9041c-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9041c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9041c-115">Requirements</span></span>  
 <span data-ttu-id="9041c-116">**Nagłówek:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="9041c-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9041c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9041c-117">See also</span></span>

- [<span data-ttu-id="9041c-118">INotifySink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9041c-118">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="9041c-119">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="9041c-119">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
