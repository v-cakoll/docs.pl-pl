---
title: Funkcja BlessIWbemServices (niezarządzany wykaz interfejsów API)
description: Funkcja BlessIWbemServices wskazuje, czy poświadczenia użytkownika zezwolić na dostęp do klasy IWbemServices.
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
ms.openlocfilehash: a65c3c14507b2520c69875a1bc101ce826ace7ba
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041411"
---
# <a name="blessiwbemservices-function"></a>Funkcja BlessIWbemServices
Wskazuje, czy poświadczenia użytkownika zezwolić na dostęp do określonego [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) klasy.   
  
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

`pIWbemServices`  
[in] Wskaźnik do [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiektu, dla których wymagane są uprawnienia.

`strUser`  
[in] Nazwa użytkownika.

`strPassword`  
[in] Hasło skojarzone z `strUser`.

`strAuthority` [in] Nazwa domeny użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`impLevel` [in] Poziom personifikacji.

`authnLevel` [in] Poziom autoryzacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WinError.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden lub więcej argumentów są nieprawidłowe. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` jest `null`. | 
| `E_FAIL` | 0x80000008 | Wystąpił nieokreślony błąd. |
| `E_OUTOFMEMORY` | 0x80000002 | Ma wystarczającej ilości pamięci do wykonania tej operacji. | 
| `S_OK` | 0 | Wywołanie funkcji zakończyło się pomyślnie. | 

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
