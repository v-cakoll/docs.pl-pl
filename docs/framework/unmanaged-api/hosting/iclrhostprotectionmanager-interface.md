---
title: "ICLRHostProtectionManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager
helpviewer_keywords: ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c88279eb26b819adaaaf86dcf59105c6ac728017
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="e4324-102">ICLRHostProtectionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e4324-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="e4324-103">Umożliwia hosta blokowanie określonych klas zarządzanych, metody, właściwości i pola w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="e4324-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4324-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e4324-104">Methods</span></span>  
  
|<span data-ttu-id="e4324-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e4324-105">Method</span></span>|<span data-ttu-id="e4324-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e4324-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4324-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="e4324-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="e4324-108">Zapewnia gwarancję, że nigdy nie przychodzą niektórych wyścigu rzadkich, które mogą spowodować krytyczny wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) błędy.</span><span class="sxs-lookup"><span data-stu-id="e4324-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="e4324-109">SetProtectedCategories — metoda</span><span class="sxs-lookup"><span data-stu-id="e4324-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="e4324-110">Określa kategorii typy zarządzane i elementów członkowskich, które powinny zostać zablokowane w częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="e4324-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4324-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4324-111">Requirements</span></span>  
 <span data-ttu-id="e4324-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4324-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4324-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4324-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4324-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4324-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4324-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4324-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4324-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4324-116">See Also</span></span>  
 [<span data-ttu-id="e4324-117">EApiCategories — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e4324-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="e4324-118">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="e4324-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
