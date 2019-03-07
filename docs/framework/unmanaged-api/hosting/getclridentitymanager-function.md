---
title: GetCLRIdentityManager — Funkcja
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea711cc03716f4cd0a06a96208da942a69f36d66
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471683"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="dc753-102">GetCLRIdentityManager — Funkcja</span><span class="sxs-lookup"><span data-stu-id="dc753-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="dc753-103">Pobiera wskaźnik do interfejsu, który umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do zarządzania tożsamościami.</span><span class="sxs-lookup"><span data-stu-id="dc753-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="dc753-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc753-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc753-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc753-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc753-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc753-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="dc753-107">[in] Element `REFIID` (identyfikator interfejsu), który określa interfejs, które można pobrać.</span><span class="sxs-lookup"><span data-stu-id="dc753-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="dc753-108">Ta wartość musi być IID_ICLRAssemblyIdentityManager lub IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="dc753-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="dc753-109">[out] Wskaźnik na adres albo [iclrassemblyidentitymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) lub [iclrhostbindingpolicymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="dc753-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc753-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc753-110">Remarks</span></span>  
 <span data-ttu-id="dc753-111">Wywołaj [getrealprocaddress —](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkcję, aby uzyskać wskaźnik do `GetCLRIdentityManager` funkcji.</span><span class="sxs-lookup"><span data-stu-id="dc753-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc753-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc753-112">Requirements</span></span>  
 <span data-ttu-id="dc753-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc753-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc753-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc753-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc753-115">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="dc753-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="dc753-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc753-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc753-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc753-117">See also</span></span>
- [<span data-ttu-id="dc753-118">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dc753-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
