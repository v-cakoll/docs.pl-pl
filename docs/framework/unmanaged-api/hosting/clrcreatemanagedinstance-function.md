---
title: ClrCreateManagedInstance — Funkcja
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f82303a3d38e7a5baaf1c3edcc41518228360d34
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088460"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="03ccf-102">ClrCreateManagedInstance — Funkcja</span><span class="sxs-lookup"><span data-stu-id="03ccf-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="03ccf-103">Tworzy wystąpienie określonego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="03ccf-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="03ccf-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03ccf-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="03ccf-105">Użyj aktywacji COM do utworzenia wystąpienia typu zarządzanego lub hostingu (zobacz [CLR hostingu interfejsów dodany do programu .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="03ccf-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03ccf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="03ccf-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03ccf-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="03ccf-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="03ccf-108">[in] Wskaźnik na nazwę żądanego typu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="03ccf-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="03ccf-109">[in] `IID` Żądana wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="03ccf-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="03ccf-110">[out] Wskaźnik do wskaźnika do wystąpienia typu zarządzanego, które zostało zażądane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="03ccf-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03ccf-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03ccf-111">Remarks</span></span>  
 <span data-ttu-id="03ccf-112">Środowisko uruchomieniowe języka wspólnego już powinny być załadowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="03ccf-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="03ccf-113">Na przykład może być załadowany za pomocą wywołania [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) działać przed `ClrCreateManagedInstance` funkcja jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="03ccf-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="03ccf-114">Jeśli środowisko wykonawcze nie został załadowany, `ClrCreateManagedInstance` po raz pierwszy próbuje załadować v1.0.3705 środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="03ccf-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="03ccf-115">W przypadku niepowodzenia próbuje załadować najnowszą wersję środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="03ccf-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03ccf-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03ccf-116">Requirements</span></span>  
 <span data-ttu-id="03ccf-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03ccf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03ccf-118">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03ccf-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03ccf-119">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03ccf-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03ccf-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03ccf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ccf-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03ccf-121">See also</span></span>

- [<span data-ttu-id="03ccf-122">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="03ccf-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="03ccf-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="03ccf-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
