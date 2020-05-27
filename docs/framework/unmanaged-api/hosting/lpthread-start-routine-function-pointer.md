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
ms.openlocfilehash: 84cdb42b11ad70f54f21ae36ca2734dc794d06d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008472"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="dac08-102">LPTHREAD_START_ROUTINE — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="dac08-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="dac08-103">Wskazuje funkcję, która powiadamia hosta o rozpoczęciu wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="dac08-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="dac08-104">Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dac08-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac08-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dac08-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dac08-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dac08-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="dac08-107">podczas Wskaźnik do kodu, który rozpoczął wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="dac08-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dac08-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dac08-108">Remarks</span></span>  
 <span data-ttu-id="dac08-109">Funkcja, do której `LPTHREAD_START_ROUTINE` punkty jest funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="dac08-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dac08-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dac08-110">Requirements</span></span>  
 <span data-ttu-id="dac08-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dac08-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dac08-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dac08-113">**Biblioteka:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="dac08-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="dac08-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dac08-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac08-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dac08-115">See also</span></span>

- [<span data-ttu-id="dac08-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dac08-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
