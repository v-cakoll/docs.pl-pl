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
ms.openlocfilehash: 97aded59f880412a6a26e7e3d664c50ff1c2f103
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557412"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="0d938-102">MALLOC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0d938-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="0d938-103">Zawiera wartości, które określają właściwości pamięci, która jest przydzielane.</span><span class="sxs-lookup"><span data-stu-id="0d938-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d938-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d938-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="0d938-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0d938-105">Members</span></span>  
  
|<span data-ttu-id="0d938-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0d938-106">Member</span></span>|<span data-ttu-id="0d938-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0d938-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="0d938-108">Ilość przydzielonej pamięci może zawierać plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="0d938-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="0d938-109">Ilość przydzielonej pamięci jest metodą o bezpiecznych wątkach.</span><span class="sxs-lookup"><span data-stu-id="0d938-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="0d938-110">Oznacza to, że pamięć jest możliwy przez wiele wątków, bez żadnej synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="0d938-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="0d938-111">Jeśli ta flaga nie jest ustawiona, wywołania do obiektu, trzeba go serializować.</span><span class="sxs-lookup"><span data-stu-id="0d938-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d938-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d938-112">Requirements</span></span>  
 <span data-ttu-id="0d938-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d938-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d938-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d938-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d938-115">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d938-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d938-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d938-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d938-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d938-117">See also</span></span>
- [<span data-ttu-id="0d938-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0d938-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
