---
title: Funkcja PutMethod (niezarządzany wykaz interfejsów API)
description: Funkcja PutMethod tworzy metodę.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cdf34ff6ae506ba209300685da3752820b250a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516753"
---
# <a name="putmethod-function"></a>PutMethod — funkcja
Tworzy metodę.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`wszName`  
[in] Nazwa metody do utworzenia. 

`lFlags`  
[in] Zastrzeżone. Ten parametr musi być 0.

`pSignatureIn`  
[in] Wskaźnik do kopię [klasy systemu __Parameters](/windows/desktop/WmiSdk/--parameters) zawierający `in` parametrów dla metody. Ten parametr jest ignorowany, jeśli ustawiono `null`.  

`pSignatureOut`  
[in]  Wskaźnik do kopię [klasy systemu __Parameters](/windows/desktop/WmiSdk/--parameters) zawierający `out` parametrów dla metody. Ten parametr jest ignorowany, jeśli ustawiono `null`.
 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów są nieprawidłowe. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]` Parametru metody, określona w obu *pInSignature* i *pOutSignature* obiekty mają różne kwalifikatorów.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Parametr metody brakuje specyfikacji **identyfikator** kwalifikator. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Serii identyfikator, która jest przypisana do parametrów metody nie jest kolejnych lub nie rozpoczyna się od 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Wartość zwracana dla metody ma **identyfikator** kwalifikator. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Nastąpiła próba ponownego użycia istniejącej nazwy metody z klasy nadrzędnej, a podpisy jest niezgodny. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.

Wywołanie tej metody jest obsługiwana tylko wtedy, gdy `ptr` jest definicją klasy modelu wspólnych informacji. Metoda manipulowania nie jest dostępna z [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) wskaźniki prowadzące do wystąpienia modelu CIM.

Użytkownicy nie mogą tworzyć metody z nazwami będącymi zaczynać się ani kończyć znakiem podkreślenia. Jest on zarezerwowany dla klas systemowych i właściwości.

Dla metody `in` i `out` parametry są określane jako właściwości w [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) obiektów.

`[in/out]` Można zdefiniować, dodając tę samą właściwość do obu obiektów wskazywany przez parametr `pInSignature` i `pOutSignature` parametrów. W tym przypadku właściwości współużytkować ten sam **identyfikator** wartość kwalifikatora.

Każdej właściwości w [__Parameters](/windows/desktop/WmiSdk/--parameters) klasy obiektów innych niż `ReturnValue` musi mieć **identyfikator** kwalifikator, zaczynający się od zera wartość liczbowa, która określa kolejność, w jakiej są wyświetlane parametry. Nie dwa parametry można mieć taką samą **identyfikator** wartości i nie **identyfikator** wartość może zostać pominięte. W przypadku obu warunku `PutMethod` funkcja zwraca `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
