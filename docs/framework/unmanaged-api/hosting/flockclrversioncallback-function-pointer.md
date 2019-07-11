---
title: FLockClrVersionCallback — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46e3356df6578f2adf2ceee00b1363b65fd014ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760229"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="fafb4-102">FLockClrVersionCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="fafb4-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="fafb4-103">Wskazuje funkcję, która Typowe wywołania środowiska uruchomieniowego (języka wspólnego CLR) języka, aby wskazać, że inicjowanie uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="fafb4-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="fafb4-104">Ten wskaźnik funkcji jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fafb4-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fafb4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fafb4-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="fafb4-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fafb4-106">Remarks</span></span>  
 <span data-ttu-id="fafb4-107">Ta funkcja jest zaimplementowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="fafb4-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fafb4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fafb4-108">Requirements</span></span>  
 <span data-ttu-id="fafb4-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fafb4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fafb4-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fafb4-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fafb4-111">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="fafb4-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="fafb4-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fafb4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fafb4-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fafb4-113">See also</span></span>

- [<span data-ttu-id="fafb4-114">LockClrVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="fafb4-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="fafb4-115">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="fafb4-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
