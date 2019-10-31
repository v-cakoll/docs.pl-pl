---
title: GetDemultiplexedStub — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetDemultiplexedStub tworzy ujścia usługi przesyłania dalej obiektów, aby pomóc klientowi w odbieraniu asynchronicznych wywołań z usługi zarządzania systemem Windows.
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
ms.openlocfilehash: 9cc028b3300b43f8a0fb3e29f8b5ac6e1817b8c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127469"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="d347b-103">GetDemultiplexedStub, funkcja</span><span class="sxs-lookup"><span data-stu-id="d347b-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="d347b-104">Tworzy obiekt sink usługi przesyłania dalej obiektów, który pomaga klientowi odbierać asynchroniczne wywołania z usługi Windows Management.</span><span class="sxs-lookup"><span data-stu-id="d347b-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d347b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d347b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="d347b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d347b-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="d347b-107">podczas Wskaźnik do implementacji w procesie klienta [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="d347b-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="d347b-108">podczas Flaga wskazująca, czy zdarzenie jest lokalne (`true`); w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d347b-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="d347b-109">określoną Obiekt sink usługi przesyłania dalej obiektów, który ułatwia Klientowi otrzymywanie wywołań asynchronicznych z usługi Windows Management.</span><span class="sxs-lookup"><span data-stu-id="d347b-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="d347b-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d347b-110">Return value</span></span>

<span data-ttu-id="d347b-111">Jeśli funkcja się powiedzie, wartość zwracana jest `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="d347b-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="d347b-112">Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero.</span><span class="sxs-lookup"><span data-stu-id="d347b-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="d347b-113">Aby uzyskać rozszerzone informacje o błędzie, wywołaj funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="d347b-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="d347b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d347b-114">Requirements</span></span>  
 <span data-ttu-id="d347b-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d347b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d347b-116">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="d347b-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d347b-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d347b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d347b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d347b-118">See also</span></span>

- [<span data-ttu-id="d347b-119">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d347b-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
