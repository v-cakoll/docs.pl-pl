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
ms.openlocfilehash: 3c6def32c63e3557a4de72baf7b1c3e67feb4891
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136528"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="af560-102">GetCLRIdentityManager — Funkcja</span><span class="sxs-lookup"><span data-stu-id="af560-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="af560-103">Pobiera wskaźnik do interfejsu, który umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do zarządzania tożsamościami.</span><span class="sxs-lookup"><span data-stu-id="af560-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="af560-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="af560-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af560-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="af560-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af560-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="af560-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="af560-107">podczas `REFIID` (identyfikator interfejsu), który określa interfejs do pobrania.</span><span class="sxs-lookup"><span data-stu-id="af560-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="af560-108">Ta wartość musi być równa IID_ICLRAssemblyIdentityManager lub IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="af560-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="af560-109">określoną Wskaźnik do adresu obiektu [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) lub [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="af560-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af560-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af560-110">Remarks</span></span>  
 <span data-ttu-id="af560-111">Wywołaj funkcję [GetRealProcAddress —](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) , aby uzyskać wskaźnik do funkcji `GetCLRIdentityManager`.</span><span class="sxs-lookup"><span data-stu-id="af560-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af560-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af560-112">Requirements</span></span>  
 <span data-ttu-id="af560-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af560-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af560-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af560-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af560-115">**Biblioteka:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="af560-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="af560-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af560-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af560-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af560-117">See also</span></span>

- [<span data-ttu-id="af560-118">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="af560-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
