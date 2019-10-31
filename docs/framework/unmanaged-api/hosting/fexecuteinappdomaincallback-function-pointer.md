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
ms.openlocfilehash: 970468bc2f50144c62c6e3cbcf9c00c2027f7663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138180"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="355ef-102">FExecuteInAppDomainCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="355ef-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="355ef-103">Wskazuje funkcję, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="355ef-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="355ef-104">Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="355ef-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="355ef-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="355ef-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="355ef-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="355ef-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="355ef-107">podczas Wskaźnik do nieprzezroczystej pamięci przydzielonyj przez obiekt wywołujący, który zawiera zarządzany kod do wykonania.</span><span class="sxs-lookup"><span data-stu-id="355ef-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="355ef-108">Alokacja i okres istnienia tej pamięci są kontrolowane przez obiekt wywołujący (czyli CLR).</span><span class="sxs-lookup"><span data-stu-id="355ef-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="355ef-109">To nie jest pamięć sterty zarządzanej przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="355ef-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="355ef-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="355ef-110">Requirements</span></span>  
 <span data-ttu-id="355ef-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="355ef-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="355ef-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="355ef-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="355ef-113">**Biblioteka:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="355ef-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="355ef-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="355ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="355ef-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="355ef-115">See also</span></span>

- [<span data-ttu-id="355ef-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="355ef-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
