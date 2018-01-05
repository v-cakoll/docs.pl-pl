---
title: "Funkcja PutMethod (niezarządzany wykaz interfejsów API)"
description: "Funkcja PutMethod tworzy metodę."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutMethod
helpviewer_keywords: PutMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e97ffcf44a738234f67d9736382c46c42e5b61e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="putmethod-function"></a>Funkcja PutMethod
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
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`wszName`  
[in] Nazwa metody do utworzenia. 

`lFlags`  
[in] Zastrzeżone. Ten parametr musi wynosić 0.

`pSignatureIn`  
[in] Wskaźnik do kopię [klasy systemu __Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) zawierający `in` parametry metody. Ten parametr jest ignorowana, jeśli ustawiono `null`.  

`pSignatureOut`  
[in]  Wskaźnik do kopię [klasy systemu __Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) zawierający `out` parametry metody. Ten parametr jest ignorowana, jeśli ustawiono `null`.
 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów nie są prawidłowe. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]` Określony zarówno parametr metody *pInSignature* i *pOutSignature* obiekty mają różne kwalifikatorów.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Parametr metody jest Brak specyfikacji **identyfikator** kwalifikatora. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Serii identyfikator, która jest przypisana do parametry metody nie jest kolejnych lub nie rozpoczynają się od 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Wartość zwracana dla metody ma **identyfikator** kwalifikatora. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Podjęto próbę ponownego użycia istniejącej nazwy metody z klasy nadrzędnej, a podpisy nie jest zgodny. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) metody.

Wywołanie tej metody jest obsługiwana tylko, jeśli `ptr` jest definicję klasy modelu wspólnych informacji. Metoda manipulowania nie jest dostępna z [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) wskaźników, które wskazują wystąpienia modelu CIM.

Użytkownicy nie mogą tworzyć metody o nazwach rozpoczynać się ani kończyć się od znaku podkreślenia. Jest to zarezerwowana dla systemu klas i właściwości.

W przypadku metody `in` i `out` parametry są opisane jako właściwości [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) obiektów.

`[in/out]` Dodając oba obiekty wskazywanej przez tę samą właściwość można zdefiniować parametr `pInSignature` i `pOutSignature` parametrów. W takim przypadku udziału takie same właściwości **identyfikator** wartość kwalifikatora.

Każdej właściwości w [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) innych niż klasa obiektu `ReturnValue` musi mieć **identyfikator** kwalifikator, wartość liczbową liczony od zera, który określa kolejność wyświetlania parametrów. Nie dwa parametry mają takie same **identyfikator** wartość i nie **identyfikator** wartość może być pominięte. W przypadku obu warunku `PutMethod` funkcja zwraca `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Przykład

Na przykład zobacz [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
