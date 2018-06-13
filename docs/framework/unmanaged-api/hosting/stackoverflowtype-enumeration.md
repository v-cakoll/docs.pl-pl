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
ms.openlocfilehash: 9e888b2359336c68ea6fdf52f798145fda12002e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440872"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="3d280-102">StackOverflowType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3d280-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="3d280-103">Zawiera wartości, które wskazują podstawową przyczyną wydarzenia przepełnienie stosu.</span><span class="sxs-lookup"><span data-stu-id="3d280-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d280-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d280-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="3d280-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3d280-105">Members</span></span>  
  
|<span data-ttu-id="3d280-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3d280-106">Member</span></span>|<span data-ttu-id="3d280-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3d280-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="3d280-108">Przepełnienie stosu spowodowane przez aparat wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3d280-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="3d280-109">Przepełnienie stosu spowodowane przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="3d280-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="3d280-110">Przepełnienie stosu spowodowane przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="3d280-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d280-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d280-111">Remarks</span></span>  
 <span data-ttu-id="3d280-112">Te informacje są przesyłane do hosta przez wywołanie [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3d280-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d280-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d280-113">Requirements</span></span>  
 <span data-ttu-id="3d280-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d280-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d280-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d280-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d280-116">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d280-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d280-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d280-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d280-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d280-118">See Also</span></span>  
 [<span data-ttu-id="3d280-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3d280-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
