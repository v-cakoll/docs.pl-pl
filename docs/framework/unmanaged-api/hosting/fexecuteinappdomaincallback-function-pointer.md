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
ms.openlocfilehash: 6fd7a19d9fc77b43bbceb1b5e5399a455429e700
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616155"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="a1ba2-102">FExecuteInAppDomainCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="a1ba2-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="a1ba2-103">Wskazuje funkcję, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a1ba2-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="a1ba2-104">Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a1ba2-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ba2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1ba2-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1ba2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1ba2-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="a1ba2-107">podczas Wskaźnik do nieprzezroczystej pamięci przydzielonyj przez obiekt wywołujący, który zawiera zarządzany kod do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a1ba2-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="a1ba2-108">Alokacja i okres istnienia tej pamięci są kontrolowane przez obiekt wywołujący (czyli CLR).</span><span class="sxs-lookup"><span data-stu-id="a1ba2-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="a1ba2-109">To nie jest pamięć sterty zarządzanej przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a1ba2-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ba2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1ba2-110">Requirements</span></span>  
 <span data-ttu-id="a1ba2-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1ba2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ba2-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1ba2-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1ba2-113">**Biblioteka:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="a1ba2-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="a1ba2-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ba2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ba2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1ba2-115">See also</span></span>

- [<span data-ttu-id="a1ba2-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a1ba2-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
