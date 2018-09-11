---
title: Funkcja CompareTo (niezarządzany wykaz interfejsów API)
description: Funkcja CompareTo porównuje obiekt do innego obiektu WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bde25ae7455dd7fe35fe1a0a43bb2a6b560c0e3e
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339321"
---
# <a name="compareto-function"></a>Funkcja CompareTo
Porównuje obiekt do innego obiektu zarządzania Windows.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`flags`  
[in] Bitowa kombinacja flagi określające właściwości obiektu do rozważenia do porównania. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`pCompareTo`  

[in] Obiekt do porównania. `pcompareTo` musi być prawidłowym [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia klasy nie może być `null`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `BeginEnumeration` został utworzony bez interwencyjnego wywołania [ `EndEnumeration` ](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Obiekty są różne. |
| `WBEM_S_SAME` | 0 | Obiekty są takie same oparte na porównanie flag. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) metody.

Flagi, które mogą być przekazywane jako `lEnumFlags` argument są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie. Należy określić cech zaangażowanych w porównaniu, określając bitową kombinację następujących flag:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignoruj źródło (serwer i przestrzeni nazw, które pochodzą z). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignoruj wszystkie Kwalifikatory (w tym **klucz** i **dynamiczne**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Pomiń domyślne wartości właściwości. Ta flaga ma zastosowanie tylko do porównania z klas. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignorowanie kwalifikatora odmian. Ta flaga nadal uwzględnia kwalifikatorów, ale ignoruje różnice wersji, takich jak zasady propagacji i zastąpić ograniczenia. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignoruj wielkość liter przy porównywaniu wartości ciągu. Dotyczy to zarówno do ciągów i wartość kwalifikatora. Porównanie nazw właściwości i kwalifikator zawsze jest rozróżniana wielkość liter, niezależnie od tego, czy ta flaga jest ustawiona. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Przyjęto założenie, czy obiekty są porównywane są instanes tej samej klasy. W związku z tym ta flaga porównuje dotyczącego wystąpienia wyłącznie informacyjne. Użyj tej flagi w celu zoptymalizowania wydajności. Jeśli obiekty nie są tego samego rodzaju, wyniki są niezdefiniowane. |

Lub można określić pojedynczej flagi złożonego w następujący sposób:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Należy wziąć pod uwagę wszystkie funkcje do porównania. |

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
