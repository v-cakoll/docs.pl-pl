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
ms.openlocfilehash: 8062ab151efc6175aa68cb0563cd2ad042ee9cd8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189056"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="1bf5e-102">FLockClrVersionCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="1bf5e-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="1bf5e-103">Wskazuje funkcję, która Typowe wywołania środowiska uruchomieniowego (języka wspólnego CLR) języka, aby wskazać, że inicjowanie uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="1bf5e-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="1bf5e-104">Ten wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1bf5e-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf5e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1bf5e-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="1bf5e-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1bf5e-106">Remarks</span></span>  
 <span data-ttu-id="1bf5e-107">Ta funkcja jest zaimplementowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="1bf5e-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bf5e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1bf5e-108">Requirements</span></span>  
 <span data-ttu-id="1bf5e-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bf5e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bf5e-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1bf5e-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bf5e-111">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="1bf5e-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="1bf5e-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bf5e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf5e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bf5e-113">See also</span></span>

- [<span data-ttu-id="1bf5e-114">LockClrVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="1bf5e-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="1bf5e-115">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1bf5e-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
