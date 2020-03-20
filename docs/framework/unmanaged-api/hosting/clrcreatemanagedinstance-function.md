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
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176542"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="556a5-102">ClrCreateManagedInstance — Funkcja</span><span class="sxs-lookup"><span data-stu-id="556a5-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="556a5-103">Tworzy wystąpienie określonego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="556a5-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="556a5-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="556a5-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="556a5-105">Użyj aktywacji COM, aby utworzyć wystąpienie typu zarządzanego lub użyć hostingu (zobacz [Clr Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="556a5-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="556a5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="556a5-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="556a5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="556a5-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="556a5-108">[w] Wskaźnik do nazwy żądanego typu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="556a5-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="556a5-109">[w] Typ `IID` wystąpienia, o które się ubiega.</span><span class="sxs-lookup"><span data-stu-id="556a5-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="556a5-110">[na zewnątrz] Wskaźnik do wskaźnika do wystąpienia typu zarządzanego, który został poproszony przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="556a5-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="556a5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="556a5-111">Remarks</span></span>  
 <span data-ttu-id="556a5-112">Środowisko wykonawcze języka wspólnego należy już załadować do procesu.</span><span class="sxs-lookup"><span data-stu-id="556a5-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="556a5-113">Na przykład można go załadować za pomocą wywołania [funkcji CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) przed wywołaniem `ClrCreateManagedInstance` funkcji.</span><span class="sxs-lookup"><span data-stu-id="556a5-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="556a5-114">Jeśli środowisko wykonawcze nie `ClrCreateManagedInstance` jest ładowane, najpierw próbuje załadować v1.0.3705 środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="556a5-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="556a5-115">Jeśli to się nie powiedzie, próbuje załadować najnowszą wersję środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="556a5-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="556a5-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="556a5-116">Requirements</span></span>  
 <span data-ttu-id="556a5-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="556a5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="556a5-118">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="556a5-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="556a5-119">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="556a5-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="556a5-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="556a5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556a5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="556a5-121">See also</span></span>

- [<span data-ttu-id="556a5-122">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="556a5-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="556a5-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="556a5-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
