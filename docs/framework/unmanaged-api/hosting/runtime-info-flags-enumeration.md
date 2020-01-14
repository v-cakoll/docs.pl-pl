---
title: RUNTIME_INFO_FLAGS — Wyliczenie
ms.date: 03/30/2017
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
ms.openlocfilehash: 9d505b917c343c40c7fa2a7aecf3466578ae0a8d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936640"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="245be-102">RUNTIME_INFO_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="245be-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="245be-103">Zawiera wartości wskazujące, które informacje o środowisku uruchomieniowym języka wspólnego (CLR) powinny zostać zwrócone.</span><span class="sxs-lookup"><span data-stu-id="245be-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="245be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="245be-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="245be-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="245be-105">Members</span></span>  
  
|<span data-ttu-id="245be-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="245be-106">Member</span></span>|<span data-ttu-id="245be-107">Opis</span><span class="sxs-lookup"><span data-stu-id="245be-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="245be-108">Wskazuje, że informacje o katalogu nie powinny być uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="245be-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="245be-109">Wskazuje, że informacja o wersji nie powinna być uwzględniona.</span><span class="sxs-lookup"><span data-stu-id="245be-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="245be-110">Wskazuje, że w przypadku błędu nie powinno być wyświetlane okno dialogowe błędu.</span><span class="sxs-lookup"><span data-stu-id="245be-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="245be-111">Wskazuje, że efekty wywołania funkcji [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) z flagą SEM_FAILCRITICALERRORS powinny zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="245be-111">Indicates that the effects of calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="245be-112">Oznacza to, że w przypadku awarii zamiast pomijania należy wyświetlić okno dialogowe instalacji.</span><span class="sxs-lookup"><span data-stu-id="245be-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="245be-113">Wskazuje żądanie informacji o wersji środowiska uruchomieniowego zgodnej z AMD-64.</span><span class="sxs-lookup"><span data-stu-id="245be-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="245be-114">Wskazuje żądanie informacji o wersji środowiska uruchomieniowego zgodnej z systemem IA-64.</span><span class="sxs-lookup"><span data-stu-id="245be-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="245be-115">Wskazuje żądanie informacji o wersji środowiska uruchomieniowego zgodnej z architekturą x86.</span><span class="sxs-lookup"><span data-stu-id="245be-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="245be-116">Wskazuje, że należy uwzględnić informacje o uaktualnianiu wersji.</span><span class="sxs-lookup"><span data-stu-id="245be-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="245be-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="245be-117">Remarks</span></span>  
 <span data-ttu-id="245be-118">Poniższe flagi architektury platformy można określić tylko po jednej naraz i nie można ich łączyć:</span><span class="sxs-lookup"><span data-stu-id="245be-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="245be-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="245be-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="245be-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="245be-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="245be-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="245be-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="245be-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="245be-122">Requirements</span></span>  
 <span data-ttu-id="245be-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="245be-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="245be-124">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="245be-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="245be-125">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="245be-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="245be-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="245be-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245be-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="245be-127">See also</span></span>

- [<span data-ttu-id="245be-128">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="245be-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
