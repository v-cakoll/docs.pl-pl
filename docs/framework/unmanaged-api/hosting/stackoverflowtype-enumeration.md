---
title: "StackOverflowType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowType
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowType
helpviewer_keywords: StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64312398c95a33c2bbe136b1c4d03c06cb09aeef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="e025a-102">StackOverflowType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e025a-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="e025a-103">Zawiera wartości, które wskazują podstawową przyczyną wydarzenia przepełnienie stosu.</span><span class="sxs-lookup"><span data-stu-id="e025a-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e025a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e025a-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="e025a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e025a-105">Members</span></span>  
  
|<span data-ttu-id="e025a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e025a-106">Member</span></span>|<span data-ttu-id="e025a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e025a-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="e025a-108">Przepełnienie stosu spowodowane przez aparat wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e025a-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="e025a-109">Przepełnienie stosu spowodowane przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="e025a-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="e025a-110">Przepełnienie stosu spowodowane przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="e025a-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e025a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e025a-111">Remarks</span></span>  
 <span data-ttu-id="e025a-112">Te informacje są przesyłane do hosta przez wywołanie [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e025a-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e025a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e025a-113">Requirements</span></span>  
 <span data-ttu-id="e025a-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e025a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e025a-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e025a-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e025a-116">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e025a-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e025a-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e025a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e025a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e025a-118">See Also</span></span>  
 [<span data-ttu-id="e025a-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e025a-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
