---
title: BlessIWbemServices — funkcja (niezarządzana dokumentacja interfejsu API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57ab5eb418b5f0a9175074c87837c7cac8936346
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799044"
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices, funkcja
Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonej klasy [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) .   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
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
podczas Wskaźnik do obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , dla którego wymagane są uprawnienia.

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
| `E_POINTER` | 0x80004003 | `pIWbemServices`jest `null`. | 
| `E_FAIL` | 0x80000008 | Wystąpił nieokreślony błąd. |
| `E_OUTOFMEMORY` | 0x80000002 | Za mało dostępnej pamięci, aby wykonać tę operację. | 
| `S_OK` | 0 | Wywołanie funkcji zakończyło się pomyślnie. | 

## <a name="requirements"></a>Wymagania  

 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
