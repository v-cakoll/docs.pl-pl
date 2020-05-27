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
ms.openlocfilehash: 630fe4e79b369bfdefc19be72780f1893090895e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008459"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="8bb1c-102">MALLOC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8bb1c-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="8bb1c-103">Zawiera wartości określające charakterystyki przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb1c-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bb1c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="8bb1c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8bb1c-105">Members</span></span>  
  
|<span data-ttu-id="8bb1c-106">Członek</span><span class="sxs-lookup"><span data-stu-id="8bb1c-106">Member</span></span>|<span data-ttu-id="8bb1c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb1c-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="8bb1c-108">Przydzieloną pamięć może zawierać plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="8bb1c-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="8bb1c-109">Przydzieloną pamięć jest bezpieczna wątkowo.</span><span class="sxs-lookup"><span data-stu-id="8bb1c-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="8bb1c-110">Oznacza to, że pamięć może być dostępna przez wiele wątków bez żadnej synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="8bb1c-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="8bb1c-111">Jeśli ta flaga nie jest ustawiona, wywołania na obiekcie muszą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="8bb1c-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bb1c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bb1c-112">Requirements</span></span>  
 <span data-ttu-id="8bb1c-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bb1c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bb1c-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8bb1c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8bb1c-115">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8bb1c-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bb1c-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bb1c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb1c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb1c-117">See also</span></span>

- [<span data-ttu-id="8bb1c-118">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8bb1c-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
