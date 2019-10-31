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
ms.openlocfilehash: f1ad414c30788801e14a33e98a0893e2a0f58d0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136521"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="7551a-102">FLockClrVersionCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="7551a-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="7551a-103">Wskazuje funkcję, którą wywołuje środowisko uruchomieniowe języka wspólnego (CLR), aby wskazać, że inicjalizacja została uruchomiona lub ukończona.</span><span class="sxs-lookup"><span data-stu-id="7551a-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="7551a-104">Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7551a-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7551a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7551a-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="7551a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7551a-106">Remarks</span></span>  
 <span data-ttu-id="7551a-107">Ta funkcja jest implementowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="7551a-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7551a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7551a-108">Requirements</span></span>  
 <span data-ttu-id="7551a-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7551a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7551a-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7551a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7551a-111">**Biblioteka:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="7551a-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="7551a-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7551a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7551a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7551a-113">See also</span></span>

- [<span data-ttu-id="7551a-114">LockClrVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="7551a-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="7551a-115">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="7551a-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
