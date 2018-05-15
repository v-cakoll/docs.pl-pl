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
ms.openlocfilehash: fce759877ad5e3c9041344647781da07ad19a45a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="285e9-102">HOST_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="285e9-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="285e9-103">Zawiera wartości, które określają typ hosta, który uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="285e9-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="285e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="285e9-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="285e9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="285e9-105">Members</span></span>  
  
|<span data-ttu-id="285e9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="285e9-106">Member</span></span>|<span data-ttu-id="285e9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="285e9-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="285e9-108">Uruchom aplikację z AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="285e9-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="285e9-109">Użyj tej wartości na częściowo zaufane aplikacje.</span><span class="sxs-lookup"><span data-stu-id="285e9-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="285e9-110">Bezpośrednio uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="285e9-110">Launch the application directly.</span></span> <span data-ttu-id="285e9-111">Oznacza to uruchamianie aplikacji z pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="285e9-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="285e9-112">Użyj tej wartości dla w pełni zaufane aplikacje.</span><span class="sxs-lookup"><span data-stu-id="285e9-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="285e9-113">Taka sama jak HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="285e9-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="285e9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="285e9-114">Requirements</span></span>  
 <span data-ttu-id="285e9-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="285e9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="285e9-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="285e9-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="285e9-117">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="285e9-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="285e9-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="285e9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="285e9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="285e9-119">See Also</span></span>  
 [<span data-ttu-id="285e9-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="285e9-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
