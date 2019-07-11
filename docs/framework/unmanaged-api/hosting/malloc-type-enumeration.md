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
ms.openlocfilehash: f1c3fd9155761528b9203a5c69dee0bde16327f7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779339"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="aeba4-102">MALLOC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="aeba4-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="aeba4-103">Zawiera wartości, które określają właściwości pamięci, która jest przydzielane.</span><span class="sxs-lookup"><span data-stu-id="aeba4-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeba4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aeba4-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="aeba4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="aeba4-105">Members</span></span>  
  
|<span data-ttu-id="aeba4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="aeba4-106">Member</span></span>|<span data-ttu-id="aeba4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="aeba4-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="aeba4-108">Ilość przydzielonej pamięci może zawierać plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="aeba4-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="aeba4-109">Ilość przydzielonej pamięci jest metodą o bezpiecznych wątkach.</span><span class="sxs-lookup"><span data-stu-id="aeba4-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="aeba4-110">Oznacza to, że pamięć jest możliwy przez wiele wątków, bez żadnej synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="aeba4-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="aeba4-111">Jeśli ta flaga nie jest ustawiona, wywołania do obiektu, trzeba go serializować.</span><span class="sxs-lookup"><span data-stu-id="aeba4-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aeba4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aeba4-112">Requirements</span></span>  
 <span data-ttu-id="aeba4-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeba4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeba4-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aeba4-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeba4-115">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aeba4-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeba4-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeba4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeba4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aeba4-117">See also</span></span>

- [<span data-ttu-id="aeba4-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="aeba4-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
