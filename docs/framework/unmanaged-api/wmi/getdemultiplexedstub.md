---
title: Funkcja GetDemultiplexedStub (niezarządzany wykaz interfejsów API)
description: Funkcja GetDemultiplexedStub tworzy obiektu sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołań asynchronicznych z zarządzania Windows.
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
ms.openlocfilehash: 4311a77c9159428bf7beacc99d4479acb28b91b6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037217"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="6655a-103">GetDemultiplexedStub — funkcja</span><span class="sxs-lookup"><span data-stu-id="6655a-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="6655a-104">Tworzy obiektu sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołań asynchronicznych z zarządzania Windows.</span><span class="sxs-lookup"><span data-stu-id="6655a-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6655a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6655a-105">Syntax</span></span>  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="6655a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6655a-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="6655a-107">[in] Wskaźnik do klienta w trakcie wykonania [funkcji IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="6655a-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="6655a-108">[in] Flagę wskazującą, czy zdarzenie jest lokalny (`true`); w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="6655a-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="6655a-109">[out] Obiektu sink usługi przesyłania dalej pomagać klientowi w odbieranie wywołań asynchronicznych z zarządzania Windows.</span><span class="sxs-lookup"><span data-stu-id="6655a-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="6655a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6655a-110">Return value</span></span>

<span data-ttu-id="6655a-111">Jeśli funkcja się powiedzie, wartość zwracana jest `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="6655a-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="6655a-112">Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera.</span><span class="sxs-lookup"><span data-stu-id="6655a-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="6655a-113">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="6655a-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="6655a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6655a-114">Requirements</span></span>  
 <span data-ttu-id="6655a-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6655a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6655a-116">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6655a-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6655a-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6655a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6655a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6655a-118">See also</span></span>  
[<span data-ttu-id="6655a-119">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="6655a-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
