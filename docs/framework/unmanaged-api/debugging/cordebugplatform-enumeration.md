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
ms.openlocfilehash: 03b6f1b29157889d0e84e5dddc94d5e3ae27efce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180945"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="0b379-102">Wyliczenie CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="0b379-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="0b379-103">Udostępnia wartości platformy docelowe, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0b379-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b379-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b379-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="0b379-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0b379-105">Members</span></span>  
  
|<span data-ttu-id="0b379-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0b379-106">Member</span></span>|<span data-ttu-id="0b379-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0b379-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0b379-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="0b379-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="0b379-109">Platforma docelowa jest sprzęt firmy Intel x86 z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="0b379-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="0b379-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="0b379-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="0b379-111">Platforma docelowa jest Windows 64-bitowym systemem AMD64 lub obsługą technologii Intel EM64T sprzętu.</span><span class="sxs-lookup"><span data-stu-id="0b379-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="0b379-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="0b379-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="0b379-113">Platforma docelowa jest 32-bitowa Windows uruchomionej na sprzęcie Intel IA-64.</span><span class="sxs-lookup"><span data-stu-id="0b379-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="0b379-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="0b379-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="0b379-115">Platforma docelowa jest uruchomionej na sprzęcie PowerPC systemu operacyjnego dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="0b379-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="0b379-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="0b379-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="0b379-117">Platforma docelowa jest uruchomionego na sprzęt firmy Intel x86 systemu operacyjnego dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="0b379-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="0b379-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="0b379-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="0b379-119">Platforma docelowa jest uruchomionego na ARM Windows sprzętu systemu operacyjnego dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="0b379-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="0b379-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="0b379-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="0b379-121">Platformą docelową jest system operacyjny dla komputerów Macintosh uruchomionej na sprzęcie AMD64.</span><span class="sxs-lookup"><span data-stu-id="0b379-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b379-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b379-122">Requirements</span></span>  
 <span data-ttu-id="0b379-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b379-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b379-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b379-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b379-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b379-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0b379-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0b379-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 <span data-ttu-id="0b379-127">`CORDB_PLATFORM_WINDOWS_ARM` i `CORDB_PLATFORM_MAC_AMD64` składowe są dostępne w programie .NET Framework 4.5.2 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="0b379-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b379-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b379-128">See also</span></span>

- [<span data-ttu-id="0b379-129">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0b379-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
