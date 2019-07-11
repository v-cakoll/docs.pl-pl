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
ms.openlocfilehash: 2823c018ff22607052cb9a298f69dbd0c4fe2c23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769500"
---
# <a name="callid-structure"></a><span data-ttu-id="4715b-102">CALL_ID — Struktura</span><span class="sxs-lookup"><span data-stu-id="4715b-102">CALL_ID Structure</span></span>
<span data-ttu-id="4715b-103">Informacje debugera o funkcję, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="4715b-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="4715b-104">Zobacz [inotifysink2 —](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interfejsu, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="4715b-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4715b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4715b-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4715b-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4715b-106">Members</span></span>  
  
|<span data-ttu-id="4715b-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4715b-107">Member</span></span>|<span data-ttu-id="4715b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4715b-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="4715b-109">Identyfikuje komputer, który wykonuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="4715b-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="4715b-110">Określa procesor maszyny.</span><span class="sxs-lookup"><span data-stu-id="4715b-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="4715b-111">Identyfikuje wątku, który wykonuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="4715b-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="4715b-112">Określa adres stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="4715b-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="4715b-113">Określa adres wywołania.</span><span class="sxs-lookup"><span data-stu-id="4715b-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="4715b-114">Identyfikuje komputer, na którym będą wykonywane wywołanie.</span><span class="sxs-lookup"><span data-stu-id="4715b-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4715b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4715b-115">Requirements</span></span>  
 <span data-ttu-id="4715b-116">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="4715b-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4715b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4715b-117">See also</span></span>

- [<span data-ttu-id="4715b-118">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4715b-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="4715b-119">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="4715b-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
