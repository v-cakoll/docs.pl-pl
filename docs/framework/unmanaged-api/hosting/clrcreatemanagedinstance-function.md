---
title: "ClrCreateManagedInstance — Funkcja"
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
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64a1bc6bbd89e3a36ac53b322bb246a7e61baa67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="e3389-102">ClrCreateManagedInstance — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e3389-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="e3389-103">Tworzy wystąpienie określonego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e3389-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="e3389-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3389-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="e3389-105">Użyj aktywacji COM. można utworzyć wystąpienia typu zarządzanego lub hosting (zobacz [CLR hostingu interfejsów dodany do programu .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="e3389-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3389-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3389-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3389-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3389-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="e3389-108">[in] Wskaźnik do nazwa żądanego typu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e3389-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="e3389-109">[in] `IID` Żądanego typu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e3389-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="e3389-110">[out] Wskaźnik na wskaźnik do wystąpienia typu zarządzanego, której zażądano przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="e3389-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3389-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3389-111">Remarks</span></span>  
 <span data-ttu-id="e3389-112">Środowisko uruchomieniowe języka wspólnego powinna już być załadowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="e3389-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="e3389-113">Na przykład mogą być ładowane przy użyciu wywołania [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcji przed `ClrCreateManagedInstance` funkcja jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="e3389-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="e3389-114">Jeśli środowisko uruchomieniowe nie został załadowany, `ClrCreateManagedInstance` po raz pierwszy próbuje załadować v1.0.3705 środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e3389-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="e3389-115">W przypadku niepowodzenia próbuje załadować najnowszą wersję środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e3389-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3389-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3389-116">Requirements</span></span>  
 <span data-ttu-id="e3389-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3389-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3389-118">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3389-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3389-119">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3389-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3389-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3389-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3389-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3389-121">See Also</span></span>  
 [<span data-ttu-id="e3389-122">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="e3389-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="e3389-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="e3389-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
