---
title: HOST_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caf76fa7962de9392b06591777ac862aa548d20d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779550"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="2006b-102">HOST_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2006b-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="2006b-103">Zawiera wartości, które określają typ hosta, który uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="2006b-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2006b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2006b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="2006b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2006b-105">Members</span></span>  
  
|<span data-ttu-id="2006b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2006b-106">Member</span></span>|<span data-ttu-id="2006b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2006b-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="2006b-108">Uruchom aplikację z AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="2006b-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="2006b-109">Użyj tej wartości dla częściowo zaufanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2006b-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="2006b-110">Uruchom aplikację bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="2006b-110">Launch the application directly.</span></span> <span data-ttu-id="2006b-111">Oznacza to uruchom aplikację w jej własnym pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="2006b-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="2006b-112">Ta wartość służy do w pełni zaufane aplikacje.</span><span class="sxs-lookup"><span data-stu-id="2006b-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="2006b-113">Taka sama jak HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="2006b-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2006b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2006b-114">Requirements</span></span>  
 <span data-ttu-id="2006b-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2006b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2006b-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2006b-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2006b-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2006b-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2006b-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2006b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2006b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2006b-119">See also</span></span>

- [<span data-ttu-id="2006b-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2006b-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
