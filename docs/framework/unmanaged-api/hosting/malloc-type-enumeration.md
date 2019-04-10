---
title: MALLOC_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 695f69c8d9c3a295a705971743733339cf8aab13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211949"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="df639-102">MALLOC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="df639-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="df639-103">Zawiera wartości, które określają właściwości pamięci, która jest przydzielane.</span><span class="sxs-lookup"><span data-stu-id="df639-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df639-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df639-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="df639-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="df639-105">Members</span></span>  
  
|<span data-ttu-id="df639-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="df639-106">Member</span></span>|<span data-ttu-id="df639-107">Opis</span><span class="sxs-lookup"><span data-stu-id="df639-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="df639-108">Ilość przydzielonej pamięci może zawierać plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="df639-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="df639-109">Ilość przydzielonej pamięci jest metodą o bezpiecznych wątkach.</span><span class="sxs-lookup"><span data-stu-id="df639-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="df639-110">Oznacza to, że pamięć jest możliwy przez wiele wątków, bez żadnej synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="df639-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="df639-111">Jeśli ta flaga nie jest ustawiona, wywołania do obiektu, trzeba go serializować.</span><span class="sxs-lookup"><span data-stu-id="df639-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df639-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df639-112">Requirements</span></span>  
 <span data-ttu-id="df639-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df639-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df639-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df639-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df639-115">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df639-115">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="df639-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="df639-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="df639-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df639-117">See also</span></span>

- [<span data-ttu-id="df639-118">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="df639-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
