---
title: Wyliczenie CorDebugPlatform
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c0644dc247225c510e1c84254417551b490416
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739663"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="077d9-102">Wyliczenie CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="077d9-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="077d9-103">Udostępnia wartości platformy docelowe, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="077d9-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="077d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="077d9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="077d9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="077d9-105">Members</span></span>  
  
|<span data-ttu-id="077d9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="077d9-106">Member</span></span>|<span data-ttu-id="077d9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="077d9-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="077d9-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="077d9-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="077d9-109">Platforma docelowa jest sprzęt firmy Intel x86 z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="077d9-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="077d9-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="077d9-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="077d9-111">Platforma docelowa jest Windows 64-bitowym systemem AMD64 lub obsługą technologii Intel EM64T sprzętu.</span><span class="sxs-lookup"><span data-stu-id="077d9-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="077d9-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="077d9-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="077d9-113">Platforma docelowa jest 32-bitowa Windows uruchomionej na sprzęcie Intel IA-64.</span><span class="sxs-lookup"><span data-stu-id="077d9-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="077d9-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="077d9-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="077d9-115">Platforma docelowa jest uruchomionej na sprzęcie PowerPC systemu operacyjnego dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="077d9-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="077d9-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="077d9-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="077d9-117">Platforma docelowa jest uruchomionego na sprzęt firmy Intel x86 systemu operacyjnego dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="077d9-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="077d9-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="077d9-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="077d9-119">Platforma docelowa jest uruchomionego na ARM Windows sprzętu systemu operacyjnego dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="077d9-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="077d9-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="077d9-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="077d9-121">Platformą docelową jest system operacyjny dla komputerów Macintosh uruchomionej na sprzęcie AMD64.</span><span class="sxs-lookup"><span data-stu-id="077d9-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="077d9-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="077d9-122">Requirements</span></span>  
 <span data-ttu-id="077d9-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="077d9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="077d9-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="077d9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="077d9-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="077d9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="077d9-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="077d9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="077d9-127">`CORDB_PLATFORM_WINDOWS_ARM` i `CORDB_PLATFORM_MAC_AMD64` składowe są dostępne w programie .NET Framework 4.5.2 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="077d9-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077d9-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="077d9-128">See also</span></span>

- [<span data-ttu-id="077d9-129">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="077d9-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
