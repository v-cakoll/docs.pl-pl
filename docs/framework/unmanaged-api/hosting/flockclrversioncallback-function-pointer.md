---
title: FLockClrVersionCallback — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: af42de820b2d835e8ea137a2643a51678e382ff0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617285"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="418c7-102">FLockClrVersionCallback — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="418c7-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="418c7-103">Wskazuje funkcję, którą wywołuje środowisko uruchomieniowe języka wspólnego (CLR), aby wskazać, że inicjalizacja została uruchomiona lub ukończona.</span><span class="sxs-lookup"><span data-stu-id="418c7-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="418c7-104">Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="418c7-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="418c7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="418c7-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="418c7-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="418c7-106">Remarks</span></span>  
 <span data-ttu-id="418c7-107">Ta funkcja jest implementowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="418c7-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="418c7-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="418c7-108">Requirements</span></span>  
 <span data-ttu-id="418c7-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="418c7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="418c7-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="418c7-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="418c7-111">**Biblioteka:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="418c7-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="418c7-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="418c7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="418c7-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="418c7-113">See also</span></span>

- [<span data-ttu-id="418c7-114">LockClrVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="418c7-114">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="418c7-115">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="418c7-115">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
