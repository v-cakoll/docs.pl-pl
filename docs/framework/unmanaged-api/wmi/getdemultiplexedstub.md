---
title: Funkcja GetDemultiplexedStub (niezarządzany wykaz interfejsów API)
description: Funkcja GetDemultiplexedStub tworzy obiekt sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołania asynchroniczne z zarządzania systemu Windows.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b195d3a512c537ca409bd2039add9e69abaf4df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="77735-103">Funkcja GetDemultiplexedStub</span><span class="sxs-lookup"><span data-stu-id="77735-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="77735-104">Tworzy obiekt sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołania asynchroniczne z zarządzania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="77735-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="77735-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="77735-105">Syntax</span></span>  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="77735-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="77735-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="77735-107">[in] Wskaźnik do klienta w trakcie stosowania [funkcji IWbemObjectSink](https://msdn.microsoft.com/library/aa391787(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="77735-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](https://msdn.microsoft.com/library/aa391787(v=vs.85).aspx).</span></span>

`isLocal`  
<span data-ttu-id="77735-108">[in] Flaga, która wskazuje, czy zdarzenie jest lokalny (`true`); w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="77735-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="77735-109">[out] Obiekt sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołania asynchroniczne z zarządzania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="77735-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="77735-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="77735-110">Return value</span></span>

<span data-ttu-id="77735-111">Jeśli funkcja zakończy się powodzeniem, jest zwracana wartość `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="77735-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="77735-112">Jeśli funkcja nie powiedzie się, wartość zwracana jest kodu zera błędu.</span><span class="sxs-lookup"><span data-stu-id="77735-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="77735-113">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="77735-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="77735-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77735-114">Requirements</span></span>  
 <span data-ttu-id="77735-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77735-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77735-116">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="77735-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="77735-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="77735-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77735-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77735-118">See also</span></span>  
[<span data-ttu-id="77735-119">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="77735-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
