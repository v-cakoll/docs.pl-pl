---
title: Funkcja PutMethod (odwołanie do niezarządzanego interfejsu API)
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
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174917"
---
# <a name="putmethod-function"></a>PutMethod, funkcja
Tworzy metodę.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia  
  
```cpp  
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
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszName`  
[w] Nazwa metody do utworzenia.

`lFlags`  
[w] Zastrzeżone. Ten parametr musi być 0.

`pSignatureIn`  
[w] Wskaźnik do kopii [__Parameters klasy systemowej,](/windows/desktop/WmiSdk/--parameters) która `in` zawiera parametry metody. Ten parametr jest ignorowany, jeśli jest ustawiony na `null`.  

`pSignatureOut`  
[w]  Wskaźnik do kopii [__Parameters klasy systemowej,](/windows/desktop/WmiSdk/--parameters) która `out` zawiera parametry metody. Ten parametr jest ignorowany, jeśli jest ustawiony na `null`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Co najmniej jeden parametr jest nieprawidłowy. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Parametr `[in, out]` metody określony zarówno w *pInSignature* i *pOutSignature* obiektów mają różne kwalifikatory.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Brak specyfikacji kwalifikatora **identyfikatora** brakuje parametru metody. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Seria identyfikatorów, która jest przypisana do parametrów metody nie jest kolejna lub nie zaczyna się od 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Zwracana wartość metody ma kwalifikator **identyfikatora.** |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Podjęto próbę ponownego użycia istniejącej nazwy metody z klasy nadrzędnej, a podpisy nie były zgodne. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)

To wywołanie metody jest `ptr` obsługiwane tylko wtedy, gdy jest definicją klasy CIM. Manipulacja metodą nie jest dostępna w wskaźnikach [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazujących na wystąpienia cim.

Użytkownicy nie mogą tworzyć metod o nazwach, które rozpoczynają się lub kończą na podkreślenia. Jest to zarezerwowane dla klas systemowych i właściwości.

Dla metody `in` i `out` parametry są opisane jako właściwości w [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) obiektów.

Parametr `[in/out]` można zdefiniować, dodając tę samą właściwość `pInSignature` `pOutSignature` do obu obiektów wskazywał przez i parametrów. W takim przypadku właściwości mają tę samą wartość kwalifikatora **identyfikatora.**

Każda właściwość w [obiekcie](/windows/desktop/WmiSdk/--parameters) klasy `ReturnValue` __Parameters innej niż musi mieć kwalifikator **identyfikatora,** wartość liczbową opartą na wartości zerowej, która identyfikuje kolejność, w jakiej pojawiają się parametry. Żadne dwa parametry nie mogą mieć tej samej wartości **identyfikatora** i nie można pominąć żadnej wartości **identyfikatora.** Jeśli wystąpi którykolwiek `PutMethod` z `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`tych warunków, funkcja zwraca wartość .

## <a name="example"></a>Przykład

Na przykład zobacz [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
