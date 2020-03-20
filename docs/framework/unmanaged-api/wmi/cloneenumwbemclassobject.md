---
title: CloneEnumWbemClassObject, funkcja (niezarządzane odwołanie do interfejsu API)
description: CloneEnumWbemClassObject funkcja sprawia, że logiczna kopia modułu wyliczacza.
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
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175021"
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
[na zewnątrz] Odbiera wskaźnik do nowego [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).

`authLevel`\
[w] Poziom autoryzacji.

`impLevel`\
[w] Poziom personifikacji.

`pCurrentEnumWbemClassObject`\
[na zewnątrz] Wskaźnik do [wystąpienia IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) do sklonowania.

`strUser`\
[w] Nazwa użytkownika. Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)

`strPassword`\
[w] Hasło. Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)

`strAuthority`\
[w] Nazwa domeny użytkownika. Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpiła ogólna porażka. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna zakończyć operację. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Połączenie procedury zdalnej (RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IEnumWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)

Ta metoda sprawia, że tylko "najlepszy wysiłek" kopię. Ze względu na dynamiczny charakter wielu obiektów CIM jest możliwe, że nowy wyliczacz nie wylicza ten sam zestaw obiektów jako wyliczacz źródłowy.

Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo.](geterrorinfo.md)

## <a name="example"></a>Przykład

Na przykład zobacz [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) metody.

## <a name="requirements"></a>Wymagania
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** WMINet_Utils.idl

 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
