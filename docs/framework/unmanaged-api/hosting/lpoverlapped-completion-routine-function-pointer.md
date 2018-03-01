---
title: "LPOVERLAPPED_COMPLETION_ROUTINE — Wskaźnik funkcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9b1846cf8fff5c41fc54ddeec5b495b50c63581c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="82f70-102">LPOVERLAPPED_COMPLETION_ROUTINE — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="82f70-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="82f70-103">Wskazuje funkcji, które powiadamia hosta przy nakładających się (oznacza to, asynchroniczne) zostało ukończone operacje We/Wy na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="82f70-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="82f70-104">This, wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82f70-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f70-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="82f70-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82f70-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="82f70-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="82f70-107">[in] Wartość, która jest kod błędu, jeśli urządzenie zostało zamknięte; w przeciwnym razie ta wartość wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="82f70-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="82f70-108">Zamykanie urządzenia powoduje, że wszystkie oczekujące operacje We/Wy na urządzeniu należy natychmiast wykonać.</span><span class="sxs-lookup"><span data-stu-id="82f70-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="82f70-109">[in] Liczba bajtów przesłanych w ramach operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="82f70-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="82f70-110">[in] Wskaźnik do struktury, który zawiera informacje, które ma być używany do wykonania żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="82f70-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82f70-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82f70-111">Remarks</span></span>  
 <span data-ttu-id="82f70-112">Funkcja, do której `LPOVERLAPPED_COMPLETION_ROUTINE` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez Edytor hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82f70-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="82f70-113">Funkcja wywołania zwrotnego umożliwia hosta do przetwarzania zakończone żądanie operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="82f70-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f70-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82f70-114">Requirements</span></span>  
 <span data-ttu-id="82f70-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82f70-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f70-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82f70-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82f70-117">**Biblioteka:** Mscorwks.dll.a;a;pierwsza</span><span class="sxs-lookup"><span data-stu-id="82f70-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="82f70-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f70-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f70-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82f70-119">See Also</span></span>  
 [<span data-ttu-id="82f70-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="82f70-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
