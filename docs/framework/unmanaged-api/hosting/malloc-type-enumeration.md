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
ms.openlocfilehash: 16f56809b4db159c71b06b3bb9d969f8a8f8fc54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090824"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="b924d-102">MALLOC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b924d-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="b924d-103">Zawiera wartości określające charakterystyki przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="b924d-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b924d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b924d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="b924d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b924d-105">Members</span></span>  
  
|<span data-ttu-id="b924d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b924d-106">Member</span></span>|<span data-ttu-id="b924d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b924d-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="b924d-108">Przydzieloną pamięć może zawierać plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="b924d-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="b924d-109">Przydzieloną pamięć jest bezpieczna wątkowo.</span><span class="sxs-lookup"><span data-stu-id="b924d-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="b924d-110">Oznacza to, że pamięć może być dostępna przez wiele wątków bez żadnej synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="b924d-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="b924d-111">Jeśli ta flaga nie jest ustawiona, wywołania na obiekcie muszą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="b924d-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b924d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b924d-112">Requirements</span></span>  
 <span data-ttu-id="b924d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b924d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b924d-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b924d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b924d-115">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b924d-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b924d-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b924d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b924d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b924d-117">See also</span></span>

- [<span data-ttu-id="b924d-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b924d-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
