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
ms.openlocfilehash: fd096344c987d8901f0baab86e370abbb03528e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177778"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="bcad2-102">ICLRHostProtectionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bcad2-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="bcad2-103">Umożliwia hosta zablokować określonych zarządzanych klas, metod, właściwości i pola z uruchomionych w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="bcad2-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bcad2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bcad2-104">Methods</span></span>  
  
|<span data-ttu-id="bcad2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bcad2-105">Method</span></span>|<span data-ttu-id="bcad2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bcad2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bcad2-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="bcad2-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="bcad2-108">Zapewnia gwarancję, że niektóre rzadkich sytuacjach wyścigu, krytyczny języka wspólnego może spowodować błędy czasu wykonywania (CLR), które nigdy nie pojawią się.</span><span class="sxs-lookup"><span data-stu-id="bcad2-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="bcad2-109">SetProtectedCategories, metoda</span><span class="sxs-lookup"><span data-stu-id="bcad2-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="bcad2-110">Określa kategorie zarządzane typy i elementy członkowskie, które powinny zostać zablokowane w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="bcad2-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bcad2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bcad2-111">Requirements</span></span>  
 <span data-ttu-id="bcad2-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcad2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcad2-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bcad2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcad2-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bcad2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="bcad2-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bcad2-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bcad2-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcad2-116">See also</span></span>

- [<span data-ttu-id="bcad2-117">EApiCategories — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bcad2-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="bcad2-118">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bcad2-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
