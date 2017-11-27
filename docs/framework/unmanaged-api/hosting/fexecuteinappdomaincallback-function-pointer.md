---
title: "FExecuteInAppDomainCallback — Wskaźnik funkcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FExecuteInAppDomainCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: FExecuteInAppDomainCallback
helpviewer_keywords: FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5e6c04a964b50357dc3687f3faf5710505bae364
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="7271a-102">FExecuteInAppDomainCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="7271a-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="7271a-103">Wskazuje funkcję, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7271a-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="7271a-104">This, wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7271a-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7271a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7271a-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7271a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7271a-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="7271a-107">[in] Wskaźnik do nieprzezroczyste pamięci przydzielone przez obiekt wywołujący, zawierający kod zarządzany do wykonania.</span><span class="sxs-lookup"><span data-stu-id="7271a-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="7271a-108">Alokacja i okresem istnienia tej pamięci są kontrolowane przez obiekt wywołujący (CLR).</span><span class="sxs-lookup"><span data-stu-id="7271a-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="7271a-109">To nie jest pamięci zarządzanej sterty CLR.</span><span class="sxs-lookup"><span data-stu-id="7271a-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7271a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7271a-110">Requirements</span></span>  
 <span data-ttu-id="7271a-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7271a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7271a-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7271a-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7271a-113">**Biblioteka:** Mscorwks.dll.a;a;pierwsza</span><span class="sxs-lookup"><span data-stu-id="7271a-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="7271a-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7271a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7271a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7271a-115">See Also</span></span>  
 [<span data-ttu-id="7271a-116">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7271a-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
