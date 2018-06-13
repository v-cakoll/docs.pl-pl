---
title: CompareTo — funkcja (niezarządzany wykaz interfejsów API)
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
ms.openlocfilehash: db4431da90842f4f96a0f09a2f28dc473d956ee3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460411"
---
# <a name="compareto-function"></a>CompareTo — funkcja
Porównuje obiekt do innego obiektu zarządzania systemu Windows.  

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
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`flags`  
[in] Bitowe połączenie flagi określające właściwości obiektu wziąć pod uwagę do porównania. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`pCompareTo`  

[in] Obiekt do porównania. `pcompareTo` musi być prawidłową [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia klasy nie może być `null`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `BeginEnumeration` został utworzony bez wywołania pośredniczące [ `EndEnumeration` ](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Obiekty są różne. |
| `WBEM_S_SAME` | 0 | Obiekty są takie same oparte na flagi porównania. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) metody.

Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie. Można określić objętego Porównanie cech, podając bitowe połączenie z następujących flag:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignoruj źródło (serwer i przestrzeni nazw, które pochodzą z). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignoruj wszystkie Kwalifikatory (łącznie z **klucza** i **dynamiczne**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignoruj wartości domyślnej właściwości. Ta flaga ma zastosowanie tylko do porównania z klas. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignorowanie kwalifikatora odmian. Ta flaga nadal uwzględnia kwalifikatory, ale ignoruje różnice wersji, takie jak reguły propagacji i zastępowanie ograniczeń. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignoruj wielkość liter w porównanie wartości ciągu. Dotyczy to zarówno do ciągów i wartości kwalifikatora. Porównanie właściwości i kwalifikator nazwy zawsze jest rozróżniana wielkość liter, niezależnie od tego, czy ta flaga jest ustawiona. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Załóżmy, że są porównywane obiekty są instanes tej samej klasy. W związku z tym ta flaga porównuje tylko informacje z związane z wystąpienia. Optymalizowanie wydajności przy użyciu tej flagi. Jeśli obiekty nie znajdują się w tej samej klasy, wyniki są niezdefiniowane. |

Lub możesz określić pojedynczy flagę złożonego w następujący sposób:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Należy wziąć pod uwagę wszystkie funkcje do porównania. |

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
