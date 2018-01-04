---
title: "Funkcja GetDemultiplexedStub (niezarządzany wykaz interfejsów API)"
description: "Funkcja GetDemultiplexedStub tworzy obiekt sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołania asynchroniczne z zarządzania systemu Windows."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetDemultiplexedStub
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetDemultiplexedStub
helpviewer_keywords: GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ba7ca9941dc148444a4c605fecc8aaf150e8601
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getdemultiplexedstub-function"></a>Funkcja GetDemultiplexedStub
Tworzy obiekt sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołania asynchroniczne z zarządzania systemu Windows.
  
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
[in] Wskaźnik do klienta w trakcie stosowania [funkcji IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx).

`isLocal`  
[in] Flaga, która wskazuje, czy zdarzenie jest lokalny (`true`); w przeciwnym razie `false`.

`ppObject`  
[out] Obiekt sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołania asynchroniczne z zarządzania systemu Windows.

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja zakończy się powodzeniem, jest zwracana wartość `S_OK` (0).

Jeśli funkcja nie powiedzie się, wartość zwracana jest kodu zera błędu. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetErrorInfo](geterrorinfo.md) funkcji.
    
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
