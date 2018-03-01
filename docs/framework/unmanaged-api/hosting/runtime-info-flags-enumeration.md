---
title: "RUNTIME_INFO_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d050972857ba652ae0b40727260f681c383208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="c0b71-102">RUNTIME_INFO_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c0b71-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="c0b71-103">Zawiera wartości, które wskazują, jakie informacje o środowisko uruchomieniowe języka wspólnego (CLR) ma zostać zwrócony.</span><span class="sxs-lookup"><span data-stu-id="c0b71-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b71-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0b71-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c0b71-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c0b71-105">Members</span></span>  
  
|<span data-ttu-id="c0b71-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c0b71-106">Member</span></span>|<span data-ttu-id="c0b71-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c0b71-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="c0b71-108">Wskazuje, czy informacji katalogowych nie powinny być dołączone.</span><span class="sxs-lookup"><span data-stu-id="c0b71-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="c0b71-109">Wskazuje, że informacje o wersji nie powinny być dołączone.</span><span class="sxs-lookup"><span data-stu-id="c0b71-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="c0b71-110">Wskazuje, że nie można wyświetlić okno dialogowe błędu w przypadku awarii.</span><span class="sxs-lookup"><span data-stu-id="c0b71-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="c0b71-111">Oznacza to, że efekty wywołania metody [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) funkcji przy użyciu flagi parametr SEM_FAILCRITICALERRORS powinna zostać zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="c0b71-111">Indicates that the effects of calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="c0b71-112">Oznacza to, że okno dialogowe instalacji powinny być wyświetlane w przypadku awarii, a nie są pomijane.</span><span class="sxs-lookup"><span data-stu-id="c0b71-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="c0b71-113">Wskazuje żądanie informacji o wersji 64-zgodnej AMD środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c0b71-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="c0b71-114">Wskazuje żądanie informacji o wersji IA-64-compatible środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="c0b71-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="c0b71-115">Wskazuje żądanie informacji o x86 wersji zgodnej z funkcją środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c0b71-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="c0b71-116">Wskazuje, że informacje o uaktualnianiu wersji powinny być dołączone.</span><span class="sxs-lookup"><span data-stu-id="c0b71-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0b71-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0b71-117">Remarks</span></span>  
 <span data-ttu-id="c0b71-118">Następujące flagi architektura platformy, może być określony tylko jeden w czasie i nie można łączyć:</span><span class="sxs-lookup"><span data-stu-id="c0b71-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
-   <span data-ttu-id="c0b71-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="c0b71-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="c0b71-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="c0b71-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="c0b71-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="c0b71-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0b71-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0b71-122">Requirements</span></span>  
 <span data-ttu-id="c0b71-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0b71-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0b71-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c0b71-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0b71-125">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0b71-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0b71-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0b71-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b71-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0b71-127">See Also</span></span>  
 [<span data-ttu-id="c0b71-128">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c0b71-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
