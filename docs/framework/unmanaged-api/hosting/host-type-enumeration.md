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
ms.openlocfilehash: cc0cea10b4a209583fb7afb551a6b80d52ad7f62
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127028"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="dcb51-102">HOST_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="dcb51-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="dcb51-103">Zawiera wartości określające typ hosta, który uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="dcb51-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcb51-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="dcb51-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="dcb51-105">Members</span></span>  
  
|<span data-ttu-id="dcb51-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="dcb51-106">Member</span></span>|<span data-ttu-id="dcb51-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dcb51-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="dcb51-108">Uruchom aplikację z AppLaunch. exe.</span><span class="sxs-lookup"><span data-stu-id="dcb51-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="dcb51-109">Ta wartość jest używana w przypadku aplikacji częściowo zaufanych.</span><span class="sxs-lookup"><span data-stu-id="dcb51-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="dcb51-110">Uruchom aplikację bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="dcb51-110">Launch the application directly.</span></span> <span data-ttu-id="dcb51-111">Oznacza to, że należy uruchomić aplikację z własnego pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="dcb51-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="dcb51-112">Ta wartość jest używana w przypadku w pełni zaufanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dcb51-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="dcb51-113">Analogicznie jak HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="dcb51-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcb51-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcb51-114">Requirements</span></span>  
 <span data-ttu-id="dcb51-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcb51-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb51-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dcb51-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcb51-117">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dcb51-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcb51-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb51-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb51-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcb51-119">See also</span></span>

- [<span data-ttu-id="dcb51-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="dcb51-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
