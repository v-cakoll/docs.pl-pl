---
title: CloneEnumWbemClassObject — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja CloneEnumWbemClassObject wykonuje logiczną kopię modułu wyliczającego.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605314f94fd82d2a2cd7be105dde9e273f607bc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798697"
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject, funkcja
Tworzy logiczną kopię modułu wyliczającego, zachowując jego bieżącą pozycję w wyliczeniu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```

## <a name="parameters"></a>Parametry

`ppEnum`\
określoną Odbiera wskaźnik do nowego [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).

`authLevel`\
podczas Poziom autoryzacji.

`impLevel`\
podczas Poziom personifikacji.

`pCurrentEnumWbemClassObject`\
określoną Wskaźnik do wystąpienia [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) , który ma zostać sklonowany.

`strUser`\
podczas Nazwa użytkownika. Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.

`strPassword`\
podczas Hasło. Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.

`strAuthority`\ [in] nazwa domeny użytkownika. Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć operację. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IEnumWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .

Ta metoda zapewnia tylko kopię "najlepszej pracy". Ze względu na dynamiczny charakter wielu obiektów CIM, istnieje możliwość, że nowy moduł wyliczający nie wylicza tego samego zestawu obiektów, co źródłowy moduł wyliczający.

Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem, zobacz metodę [IEnumWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .

## <a name="requirements"></a>Wymagania
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówki** WMINet_Utils.idl

 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
