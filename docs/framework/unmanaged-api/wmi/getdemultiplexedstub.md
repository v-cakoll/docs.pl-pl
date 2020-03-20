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
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub, funkcja
Tworzy ujście usługi przesyłania dalej obiektu, aby pomóc klientowi w odbieraniu wywołań asynchronicznych z zarządzania systemem Windows.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a>Parametry

`pObject`  
[w] Wskaźnik do implementacji klienta w trakcie [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).

`isLocal`  
[w] Flaga wskazująca, czy wydarzenie`true`jest lokalne ( ); w `false`przeciwnym razie , .

`ppObject`  
[na zewnątrz] Obiekt usługi przesyłania dalej ujścia, aby pomóc klientowi w odbieraniu wywołań asynchronicznych z zarządzania systemem Windows.

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, `S_OK` zwracana wartość wynosi (0).

Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [GetErrorInfo.](geterrorinfo.md)

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
