---
title: Funkcja SpawnDerivedClass (niezarządzany wykaz interfejsów API)
description: Funkcja SpawnDerivedClass tworzy nowy obiekt, który pochodzi z obiektu.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81f4d5219865bf7f7c9e6d284d74d0c249729dfc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194425"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass — funkcja
Tworzy obiekt klasy pochodnej nowo od określonego obiektu.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi być 0.

`ppNewClass`  
[out] Otrzymuje wskaźnik do nowego obiektu definicji klasy. Jeśli wystąpi błąd, nowy obiekt nie jest zwracana, i `ppNewClass` się po lewej stronie w niezmienionej postaci. Jego wartość nie może być `null`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Zażądano Nieprawidłowa operacja, takiej jak duplikowanie klasy z wystąpienia usługi. |
| `WBEM_E_INCOMPLETE_CLASS` | Klasa źródłowa nie jest całkowicie zdefiniowano lub zarejestrowane w usłudze zarządzania Windows, więc nowej klasy pochodnej nie jest dozwolone. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` jest `null`. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) metody.

`ptr` musi być definicją klasy, która staje się klasy nadrzędnej obiektu zduplikowanych. Zwrócony obiekt staje się podklasą bieżący obiekt.

Nowy obiekt zwrócony w `ppNewClass` automatycznie wybrana zostaje pierwsza podklasę bieżącego obiektu. Nie można zastąpić to zachowanie. Nie ma żadnej innej metody, za pomocą którego można utworzyć podklasy (klas pochodnych).

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
