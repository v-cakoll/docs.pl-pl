---
title: EClrUnhandledException — Wyliczenie
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 63b07dda2293d3e05bd3c8fcdc45f20a498ea54c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616310"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="4d64c-102">EClrUnhandledException — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4d64c-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="4d64c-103">Opisuje dostępne opcje zarządzania wyjątkami, które nie są obsługiwane w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d64c-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d64c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d64c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="4d64c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4d64c-105">Members</span></span>  
  
|<span data-ttu-id="4d64c-106">Członek</span><span class="sxs-lookup"><span data-stu-id="4d64c-106">Member</span></span>|<span data-ttu-id="4d64c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4d64c-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="4d64c-108">Określa, że występuje zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="4d64c-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="4d64c-109">Proces został rozdarty.</span><span class="sxs-lookup"><span data-stu-id="4d64c-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="4d64c-110">Określa, że środowisko uruchomieniowe języka wspólnego (CLR) ignoruje Nieobsłużone wyjątki i umożliwia hostowi określenie dalszych akcji.</span><span class="sxs-lookup"><span data-stu-id="4d64c-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d64c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d64c-111">Remarks</span></span>  
 <span data-ttu-id="4d64c-112">Aby określić, że środowisko CLR zachowuje się jak wcześniejsze wersje, użyj `eHostDeterminedPolicy` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="4d64c-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d64c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d64c-113">Requirements</span></span>  
 <span data-ttu-id="4d64c-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d64c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d64c-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d64c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d64c-116">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d64c-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d64c-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d64c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d64c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d64c-118">See also</span></span>

- [<span data-ttu-id="4d64c-119">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4d64c-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="4d64c-120">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4d64c-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="4d64c-121">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d64c-121">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="4d64c-122">SetUnhandledExceptionPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="4d64c-122">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="4d64c-123">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d64c-123">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="4d64c-124">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4d64c-124">Hosting Enumerations</span></span>](hosting-enumerations.md)
