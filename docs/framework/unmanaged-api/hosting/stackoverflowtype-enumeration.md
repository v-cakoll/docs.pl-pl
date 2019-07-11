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
ms.openlocfilehash: 44d5b7fdb2908678671505649bb906c0c5f740e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751129"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="d1b64-102">StackOverflowType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d1b64-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="d1b64-103">Zawiera wartości wskazujące podstawowych przyczyn zdarzenie przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="d1b64-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1b64-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1b64-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="d1b64-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d1b64-105">Members</span></span>  
  
|<span data-ttu-id="d1b64-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d1b64-106">Member</span></span>|<span data-ttu-id="d1b64-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d1b64-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="d1b64-108">Przepełnienie stosu zostało spowodowane przez aparat wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d1b64-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="d1b64-109">Przepełnienie stosu zostało spowodowane przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="d1b64-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="d1b64-110">Przepełnienie stosu zostało spowodowane przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="d1b64-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1b64-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1b64-111">Remarks</span></span>  
 <span data-ttu-id="d1b64-112">Te informacje są przesyłane do hosta za pomocą wywołania [iactiononclrevent::ONEVENT —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d1b64-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1b64-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1b64-113">Requirements</span></span>  
 <span data-ttu-id="d1b64-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1b64-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1b64-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1b64-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1b64-116">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1b64-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1b64-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1b64-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b64-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1b64-118">See also</span></span>

- [<span data-ttu-id="d1b64-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d1b64-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
