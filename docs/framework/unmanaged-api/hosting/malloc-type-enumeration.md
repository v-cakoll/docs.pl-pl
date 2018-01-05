---
title: "MALLOC_TYPE — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MALLOC_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: MALLOC_TYPE
helpviewer_keywords: MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3f41f381266c76b267d5d3e366047fe5267c30b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="d25ef-102">MALLOC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d25ef-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="d25ef-103">Zawiera wartości, które określają właściwości pamięci, która jest przydzielane.</span><span class="sxs-lookup"><span data-stu-id="d25ef-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d25ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d25ef-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="d25ef-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d25ef-105">Members</span></span>  
  
|<span data-ttu-id="d25ef-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d25ef-106">Member</span></span>|<span data-ttu-id="d25ef-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d25ef-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="d25ef-108">Alokacji pamięci może zawierać plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="d25ef-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="d25ef-109">Alokacji pamięci jest bezpieczne wątkowo.</span><span class="sxs-lookup"><span data-stu-id="d25ef-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="d25ef-110">Oznacza to, że pamięć jest możliwy przez wiele wątków bez żadnej synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="d25ef-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="d25ef-111">Jeśli ta flaga nie jest ustawiona, wywołania dla obiekt musi być serializowany.</span><span class="sxs-lookup"><span data-stu-id="d25ef-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d25ef-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d25ef-112">Requirements</span></span>  
 <span data-ttu-id="d25ef-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d25ef-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d25ef-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d25ef-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d25ef-115">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d25ef-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d25ef-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d25ef-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d25ef-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d25ef-117">See Also</span></span>  
 [<span data-ttu-id="d25ef-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d25ef-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
