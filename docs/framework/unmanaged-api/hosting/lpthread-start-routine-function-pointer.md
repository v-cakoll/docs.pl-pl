---
title: LPTHREAD_START_ROUTINE — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 577526536e07172070a1e8a65e73fd15646681fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768347"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="d1f7a-102">LPTHREAD_START_ROUTINE — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="d1f7a-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="d1f7a-103">Wskazuje funkcję, która powiadamia hosta, który wątek rozpoczęło się wykonanie.</span><span class="sxs-lookup"><span data-stu-id="d1f7a-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="d1f7a-104">Ten wskaźnik funkcji jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d1f7a-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1f7a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1f7a-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1f7a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1f7a-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="d1f7a-107">[in] Wskaźnik do kodu, który rozpoczęła wykonywanie zadania.</span><span class="sxs-lookup"><span data-stu-id="d1f7a-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1f7a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1f7a-108">Remarks</span></span>  
 <span data-ttu-id="d1f7a-109">Funkcja, do którego `LPTHREAD_START_ROUTINE` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="d1f7a-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1f7a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1f7a-110">Requirements</span></span>  
 <span data-ttu-id="d1f7a-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1f7a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1f7a-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1f7a-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1f7a-113">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="d1f7a-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d1f7a-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1f7a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f7a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1f7a-115">See also</span></span>

- [<span data-ttu-id="d1f7a-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d1f7a-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
