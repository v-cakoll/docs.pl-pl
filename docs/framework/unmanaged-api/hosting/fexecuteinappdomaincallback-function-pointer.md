---
title: FExecuteInAppDomainCallback — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3de456bc28f51cb20ab72b3934041ec6b06ae
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490444"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="11c00-102">FExecuteInAppDomainCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="11c00-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="11c00-103">Wskazuje funkcję, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="11c00-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="11c00-104">Ten wskaźnik funkcji jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="11c00-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c00-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="11c00-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c00-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="11c00-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="11c00-107">[in] Wskaźnik do nieprzezroczyste pamięci przydzielonej przez obiekt wywołujący, zawierający kod zarządzany do wykonania.</span><span class="sxs-lookup"><span data-stu-id="11c00-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="11c00-108">Alokacji i okresie istnienia tej pamięci są kontrolowane przez obiekt wywołujący (CLR).</span><span class="sxs-lookup"><span data-stu-id="11c00-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="11c00-109">Nie jest to pamięć sterty zarządzanej CLR.</span><span class="sxs-lookup"><span data-stu-id="11c00-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c00-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11c00-110">Requirements</span></span>  
 <span data-ttu-id="11c00-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11c00-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c00-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11c00-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11c00-113">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="11c00-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="11c00-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c00-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c00-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11c00-115">See also</span></span>

- [<span data-ttu-id="11c00-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="11c00-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
