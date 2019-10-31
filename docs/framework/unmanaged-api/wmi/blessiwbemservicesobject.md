---
title: BlessIWbemServicesObject — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja BlessIWbemServicesObject wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do obiektu IWbemServices
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f77ff394668a235dd63cf0cddf71ea418a28125b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141686"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject, funkcja
Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonego obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) . 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a>Parametry

`pIWbemServices`\
podczas Wskaźnik do obiektu usługi WMI.

`strUser`\
podczas Nazwa użytkownika.

`strPassword`\
podczas Hasło skojarzone z `strUser`.

`strAuthority`\
podczas Nazwa domeny użytkownika. Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.

`impLevel`\
podczas Poziom personifikacji.

`authnLevel`\
podczas Poziom autoryzacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *Winerror. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Co najmniej jeden argument jest nieprawidłowy. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` jest `null`. | 
| `E_FAIL` | 0x80000008 | Wystąpił nieokreślony błąd. |
| `E_OUTOFMEMORY` | 0x80000002 | Za mało dostępnej pamięci, aby wykonać tę operację. | 
| `S_OK` | 0 | Wywołanie funkcji zakończyło się pomyślnie. | 

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** WMINet_Utils. idl

 **Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
