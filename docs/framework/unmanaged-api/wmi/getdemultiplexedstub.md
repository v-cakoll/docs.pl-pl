---
title: GetDemultiplexedStub, funkcja (odwołanie do interfejsu API niezarządzanego)
description: Funkcja GetDemultiplexedStub tworzy zlew obsługi klienta, aby pomóc klientowi w odbieraniu wywołań asynchronicznych z zarządzania systemem Windows.
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
ms.openlocfilehash: d15fed261db2ca2cda6dbf824dc9cb0d5c56eed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174969"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="d6a9d-103">GetDemultiplexedStub, funkcja</span><span class="sxs-lookup"><span data-stu-id="d6a9d-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="d6a9d-104">Tworzy ujście usługi przesyłania dalej obiektu, aby pomóc klientowi w odbieraniu wywołań asynchronicznych z zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="d6a9d-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d6a9d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6a9d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a><span data-ttu-id="d6a9d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6a9d-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="d6a9d-107">[w] Wskaźnik do implementacji klienta w trakcie [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="d6a9d-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="d6a9d-108">[w] Flaga wskazująca, czy wydarzenie`true`jest lokalne ( ); w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="d6a9d-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="d6a9d-109">[na zewnątrz] Obiekt usługi przesyłania dalej ujścia, aby pomóc klientowi w odbieraniu wywołań asynchronicznych z zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="d6a9d-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6a9d-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d6a9d-110">Return value</span></span>

<span data-ttu-id="d6a9d-111">Jeśli funkcja powiedzie się, `S_OK` zwracana wartość wynosi (0).</span><span class="sxs-lookup"><span data-stu-id="d6a9d-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="d6a9d-112">Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego.</span><span class="sxs-lookup"><span data-stu-id="d6a9d-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="d6a9d-113">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="d6a9d-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6a9d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6a9d-114">Requirements</span></span>  
 <span data-ttu-id="d6a9d-115">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6a9d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6a9d-116">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d6a9d-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d6a9d-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d6a9d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a9d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6a9d-118">See also</span></span>

- [<span data-ttu-id="d6a9d-119">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d6a9d-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
