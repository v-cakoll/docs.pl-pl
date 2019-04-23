---
title: StackOverflowType — Wyliczenie
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8541ea7b614ff4a6ca666f0e2549a7f50e190192
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135879"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="3e9db-102">StackOverflowType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3e9db-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="3e9db-103">Zawiera wartości wskazujące podstawowych przyczyn zdarzenie przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="3e9db-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e9db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e9db-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="3e9db-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3e9db-105">Members</span></span>  
  
|<span data-ttu-id="3e9db-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3e9db-106">Member</span></span>|<span data-ttu-id="3e9db-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3e9db-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="3e9db-108">Przepełnienie stosu zostało spowodowane przez aparat wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3e9db-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="3e9db-109">Przepełnienie stosu zostało spowodowane przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="3e9db-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="3e9db-110">Przepełnienie stosu zostało spowodowane przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="3e9db-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e9db-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e9db-111">Remarks</span></span>  
 <span data-ttu-id="3e9db-112">Te informacje są przesyłane do hosta za pomocą wywołania [iactiononclrevent::ONEVENT —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3e9db-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e9db-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e9db-113">Requirements</span></span>  
 <span data-ttu-id="3e9db-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e9db-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e9db-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e9db-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e9db-116">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e9db-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e9db-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e9db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9db-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e9db-118">See also</span></span>

- [<span data-ttu-id="3e9db-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3e9db-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
