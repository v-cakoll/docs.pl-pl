---
title: LPOVERLAPPED_COMPLETION_ROUTINE — Wskaźnik funkcji
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f957ff6949ea2335c6606eb112352a5180e2c1c8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500320"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="6ceed-102">LPOVERLAPPED_COMPLETION_ROUTINE — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="6ceed-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="6ceed-103">Wskazuje funkcję, która powiadamia hosta, gdy nakładająca (czyli asynchroniczne) we/wy na urządzeniu została zakończona.</span><span class="sxs-lookup"><span data-stu-id="6ceed-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="6ceed-104">Ten wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ceed-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ceed-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ceed-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ceed-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ceed-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="6ceed-107">[in] Wartość, która jest kod błędu, jeśli urządzenie zostało zamknięte; w przeciwnym razie ta wartość wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="6ceed-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="6ceed-108">Zamknięcie urządzenia powoduje, że wszystkie oczekujące operacje We/Wy na urządzeniu należy natychmiast wykonać.</span><span class="sxs-lookup"><span data-stu-id="6ceed-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="6ceed-109">[in] Liczba bajtów przesłanych w operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="6ceed-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="6ceed-110">[in] Wskaźnik do struktury, która zawiera informacje, które ma być używany do wykonania żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="6ceed-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ceed-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ceed-111">Remarks</span></span>  
 <span data-ttu-id="6ceed-112">Funkcja, do którego `LPOVERLAPPED_COMPLETION_ROUTINE` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="6ceed-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="6ceed-113">Funkcja wywołania zwrotnego Zezwalaj hostowi na przetwarzanie zakończone żądanie operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="6ceed-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ceed-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ceed-114">Requirements</span></span>  
 <span data-ttu-id="6ceed-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ceed-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ceed-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ceed-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ceed-117">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="6ceed-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="6ceed-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ceed-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ceed-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ceed-119">See also</span></span>
- [<span data-ttu-id="6ceed-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="6ceed-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
