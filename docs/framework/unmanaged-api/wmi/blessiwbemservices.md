---
title: Funkcja BlessIWbemServices (odwołanie do interfejsu API niezarządzanego)
description: Funkcja BlessIWbemServices wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do klasy IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176867"
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices, funkcja
Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonej klasy [IWbemServices.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Parametry

`pIWbemServices`\
[w] Wskaźnik do [obiektu IWbemServices,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) dla którego wymagane są uprawnienia.

`strUser`\
[w] Nazwa użytkownika.

`strPassword`\
[w] Hasło skojarzone `strUser`z programem .

`strAuthority`\
[w] Nazwa domeny użytkownika. Więcej informacji można znaleźć w funkcji [ConnectServerWmi.](connectserverwmi.md)

`impLevel`\
[w] Poziom personifikacji.

`authnLevel`\
[w] Poziom autoryzacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WinError.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden lub więcej argumentów jest nieprawidłowych. |
| `E_POINTER` | 0x80004003 | Parametr `pIWbemServices` ma wartość `null`. |
| `E_FAIL` | 0x80000008 | Wystąpił nieokreślony błąd. |
| `E_OUTOFMEMORY` | 0x80000002 | Niewystarczająca ilość pamięci jest dostępna do wykonania operacji. |
| `S_OK` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |

## <a name="requirements"></a>Wymagania  

 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
