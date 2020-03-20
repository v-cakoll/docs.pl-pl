---
title: WritePropertyValue, funkcja (odwołanie do interfejsu API niezarządzanego)
description: WritePropertyValue funkcja zapisuje bajty do właściwości.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174839"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue, funkcja
Zapisuje określoną liczbę bajtów do właściwości identyfikowanej przez dojście do właściwości.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemObjectAccess.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)

`lHandle`  
[w] Liczba całkowita zawierająca dojście identyfikujące tę właściwość. Dojście można pobrać, wywołując [Funkcję GetPropertyHandle.](getpropertyhandle.md)

`lNumBytes`  
[w] Liczba bajtów zapisywanych we właściwości. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`pHandle`[na zewnątrz] Wskaźnik do tablicy bajtów, która zawiera dane.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Wystąpił niezgodność typu. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie metody [IWbemClassObject::WritePropertyValue.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)

Ta funkcja służy do ustawiania`DWORD` ciągu i`QWORD` wszystkich innych danych innych niż lub innych.

Dla wartości właściwości nonstring musi `lNumBytes` być poprawny rozmiar danych określonego typu właściwości. Dla wartości właściwości `lNumBytes` ciągu musi być długość określonego ciągu w bajtach, a sam ciąg musi mieć równą długość w bajtach i być następuje ze znakiem zakończenia zerowego.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
