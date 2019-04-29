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
ms.openlocfilehash: 872164e2f48f1ef234b729b28aa9b1af1589c0fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608986"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub — funkcja
Tworzy obiektu sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołań asynchronicznych z zarządzania Windows.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>Parametry

`pObject`  
[in] Wskaźnik do klienta w trakcie wykonania [funkcji IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).

`isLocal`  
[in] Flagę wskazującą, czy zdarzenie jest lokalny (`true`); w przeciwnym razie `false`.

`ppObject`  
[out] Obiektu sink usługi przesyłania dalej pomagać klientowi w odbieranie wywołań asynchronicznych z zarządzania Windows.

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest `S_OK` (0).

Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [geterrorinfo —](geterrorinfo.md) funkcji.
    
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
