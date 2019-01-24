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
ms.openlocfilehash: 74654cf18d87fed8ad5ce9a4cd4249d56fdb4343
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693454"
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

Wywołanie tej metody jest obsługiwana tylko wtedy, gdy `ptr` jest definicją klasy modelu wspólnych informacji. Metoda manipulowania nie jest dostępna z [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźniki prowadzące do wystąpienia modelu CIM.

Użytkownicy nie mogą tworzyć metody z nazwami będącymi zaczynać się ani kończyć znakiem podkreślenia. Jest on zarezerwowany dla klas systemowych i właściwości.

Dla metody `in` i `out` parametry są określane jako właściwości w [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) obiektów.

`[in/out]` Można zdefiniować, dodając tę samą właściwość do obu obiektów wskazywany przez parametr `pInSignature` i `pOutSignature` parametrów. W tym przypadku właściwości współużytkować ten sam **identyfikator** wartość kwalifikatora.

Każdej właściwości w [__Parameters](/windows/desktop/WmiSdk/--parameters) klasy obiektów innych niż `ReturnValue` musi mieć **identyfikator** kwalifikator, zaczynający się od zera wartość liczbowa, która określa kolejność, w jakiej są wyświetlane parametry. Nie dwa parametry można mieć taką samą **identyfikator** wartości i nie **identyfikator** wartość może zostać pominięte. W przypadku obu warunku `PutMethod` funkcja zwraca `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
