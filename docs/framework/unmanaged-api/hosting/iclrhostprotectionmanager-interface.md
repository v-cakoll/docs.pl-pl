---
title: ICLRHostProtectionManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c630fcd4667c8b19c4e21335549674d32508e439
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="89131-102">ICLRHostProtectionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="89131-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="89131-103">Umożliwia hosta blokowanie określonych klas zarządzanych, metody, właściwości i pola w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="89131-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89131-104">Metody</span><span class="sxs-lookup"><span data-stu-id="89131-104">Methods</span></span>  
  
|<span data-ttu-id="89131-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="89131-105">Method</span></span>|<span data-ttu-id="89131-106">Opis</span><span class="sxs-lookup"><span data-stu-id="89131-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89131-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="89131-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="89131-108">Zapewnia gwarancję, że nigdy nie przychodzą niektórych wyścigu rzadkich, które mogą spowodować krytyczny wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) błędy.</span><span class="sxs-lookup"><span data-stu-id="89131-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="89131-109">SetProtectedCategories, metoda</span><span class="sxs-lookup"><span data-stu-id="89131-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="89131-110">Określa kategorii typy zarządzane i elementów członkowskich, które powinny zostać zablokowane w częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="89131-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89131-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89131-111">Requirements</span></span>  
 <span data-ttu-id="89131-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89131-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89131-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89131-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89131-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89131-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89131-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89131-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89131-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89131-116">See Also</span></span>  
 [<span data-ttu-id="89131-117">EApiCategories, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="89131-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="89131-118">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="89131-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
