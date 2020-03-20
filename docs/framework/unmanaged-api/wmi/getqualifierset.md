---
title: Funkcja GetQualifierSet (odwołanie do niezarządzanego interfejsu API)
description: Funkcja GetQualifierSet pobiera zestaw kwalifikator dla klasy lub wystąpienia.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176776"
---
# <a name="getqualifierset-function"></a>GetQualifierSet, funkcja
Pobiera zestaw kwalifikator dla wystąpienia klasy lub definicji klasy.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`ppQualSet`  
[na zewnątrz] Odbiera wskaźnik interfejsu, który umożliwia dostęp do kwalifikatorów obiektu klasy. `ppQualSet`nie `null`może być . Jeśli wystąpi błąd, nowy obiekt nie jest zwracany, a wskaźnik pozostaje niezmodyfikowany.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpiła ogólna porażka. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Określona metoda nie istnieje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do ukończenia operacji. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametrem `null`jest . |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::GetQualifierSet.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset)

[Wskaźnik IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umożliwia wywołującemu dodawanie, edytowanie lub usuwanie tych kwalifikatorów. Takie dodane, edytowane lub usunięte kwalifikatory mają zastosowanie do całej definicji wystąpienia lub klasy.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
