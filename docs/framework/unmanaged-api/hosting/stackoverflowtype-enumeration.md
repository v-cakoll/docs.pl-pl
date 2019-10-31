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
ms.openlocfilehash: f09c6bb79d7bd28f4d8b74237b6f343a07b79062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141472"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="80c70-102">StackOverflowType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="80c70-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="80c70-103">Zawiera wartości wskazujące podstawową przyczynę zdarzenia przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="80c70-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80c70-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="80c70-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="80c70-105">Members</span></span>  
  
|<span data-ttu-id="80c70-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="80c70-106">Member</span></span>|<span data-ttu-id="80c70-107">Opis</span><span class="sxs-lookup"><span data-stu-id="80c70-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="80c70-108">Przepełnienie stosu zostało spowodowane przez aparat wykonywania.</span><span class="sxs-lookup"><span data-stu-id="80c70-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="80c70-109">Przepełnienie stosu zostało spowodowane przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="80c70-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="80c70-110">Przepełnienie stosu zostało spowodowane przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="80c70-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80c70-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80c70-111">Remarks</span></span>  
 <span data-ttu-id="80c70-112">Te informacje są przesyłane do hosta za pomocą wywołania metody [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="80c70-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80c70-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80c70-113">Requirements</span></span>  
 <span data-ttu-id="80c70-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c70-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c70-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80c70-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80c70-116">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80c70-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80c70-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80c70-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c70-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80c70-118">See also</span></span>

- [<span data-ttu-id="80c70-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="80c70-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
