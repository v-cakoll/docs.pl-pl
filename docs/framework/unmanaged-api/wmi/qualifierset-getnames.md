---
title: Funkcja QualifierSet_GetNames (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_GetNames pobiera nazwy kwalifikatory z obiektu lub właściwości.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7c96439cf50c18e336baa70cf463b9463203290
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461181"
---
# <a name="qualifiersetgetnames-function"></a>Funkcja QualifierSet_GetNames
Pobiera nazwy wszystkich kwalifikatorów lub niektórych kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
[in] Ten parametr nie jest używana.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.

`lFlags`   
[in] Jeden z następujących flag lub wartości, które określa nazwy, w których do uwzględnienia w wyliczeniu.

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|  | 0 | Zwraca nazwy wszystkich kwalifikatorów. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwraca tylko nazwy kwalifikatory określonych bieżącą właściwość lub obiekt. <br/> Dla właściwości: zwracać tylko kwalifikatory określonego we właściwości (w tym zastąpień), a nie te kwalifikatory propagowane z definicji klasy. <br/> Dla wystąpienia obiektu: zwraca tylko nazwy kwalifikator danego wystąpienia. <br/> Dla klasy: przywrócenie tylko kwalifikatory określonych beiong klasy pochodnej.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Powrót propagowane tylko nazwy kwalifikatory z innego obiektu. <br/> Dla właściwości: zwracane tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości. <br/> Dla wystąpienia obiektu: Powrót propagowane tylko tych kwalifikatory z definicji klasy. <br/> Dla klasy: zwracane tylko nazwy kwalifikator odziedziczona z klasy nadrzędnej. |

`pstrNames` [out] Nowy `SAFEARRAY` zawierający żądanej nazwy. Tablica może mieć elementów 0. Jeśli wystąpi błąd, nowy `SAFEARRAY` nie są zwracane.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Można rozpocząć nowego wyliczenia jest za mało pamięci. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) metody.

Gdy po pobraniu Kwalifikator nazwy każdego kwalifikator będzie dostępny według nazwy przez wywołanie metody [QualifierSet_Get](qualifierset-get.md) funkcji. 

Nie jest błąd dla danego obiektu mieć zerowej kwalifikatory tak liczba parametrów w `pstrNames` przy powrocie może mieć wartość 0, mimo że funkcja zwraca `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
