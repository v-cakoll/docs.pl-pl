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
ms.openlocfilehash: e3031ce0eb6f23fdf5e5366d33ff075ea7816b0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649547"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="5529e-102">FExecuteInAppDomainCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="5529e-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="5529e-103">Wskazuje funkcję, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5529e-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="5529e-104">Ten wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5529e-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5529e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5529e-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5529e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5529e-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="5529e-107">[in] Wskaźnik do nieprzezroczyste pamięci przydzielonej przez obiekt wywołujący, zawierający kod zarządzany do wykonania.</span><span class="sxs-lookup"><span data-stu-id="5529e-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="5529e-108">Alokacji i okresie istnienia tej pamięci są kontrolowane przez obiekt wywołujący (CLR).</span><span class="sxs-lookup"><span data-stu-id="5529e-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="5529e-109">Nie jest to pamięć sterty zarządzanej CLR.</span><span class="sxs-lookup"><span data-stu-id="5529e-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5529e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5529e-110">Requirements</span></span>  
 <span data-ttu-id="5529e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5529e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5529e-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5529e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5529e-113">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="5529e-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="5529e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5529e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5529e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5529e-115">See also</span></span>
- [<span data-ttu-id="5529e-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="5529e-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
