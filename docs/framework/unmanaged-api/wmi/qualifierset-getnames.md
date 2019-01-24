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
ms.openlocfilehash: 2da6bc87a175851aa7b23b67075ce61e39f0b937
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555105"
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames — funkcja
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
[in] Ten parametr jest nieużywany.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.

`lFlags`   
[in] Jedną z następujących flag lub wartości, które określa nazwy, w których do uwzględnienia w wyliczeniu.

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|  | 0 | Zwraca nazwy wszystkich kwalifikatorów. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwróć tylko nazwy kwalifikatory określonych do bieżącej właściwości lub obiektu. <br/> Dla właściwości: Zwróć tylko kwalifikatory określone dla właściwości (w tym zastąpień), a nie kwalifikatory propagowane z poziomu definicji klasy. <br/> W przypadku wystąpienia: Zwróć tylko nazwy kwalifikator danego wystąpienia. <br/> Dla klasy: Zwróć tylko kwalifikatory określonych beiong klasy pochodnej.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Zwróć tylko nazwy kwalifikatory propagowane z innego obiektu. <br/> Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości. <br/> W przypadku wystąpienia: Zwróć tylko tych kwalifikatory propagowane z poziomu definicji klasy. <br/> Dla klasy: Zwróć tylko nazwy kwalifikator dziedziczone z klasy nadrzędnej. |

`pstrNames` [out] Nowy `SAFEARRAY` zawierający żądanej nazwy. Tablica może mieć elementów 0. Jeśli wystąpi błąd, nowy `SAFEARRAY` nie jest zwracana.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) metody.

Po po pobraniu nazwy kwalifikator, są dostępne każdego kwalifikator według nazwy przez wywołanie metody [QualifierSet_Get](qualifierset-get.md) funkcji. 

Nie jest błąd dla danego obiektu, który ma zero kwalifikatorów, więc liczba ciągów w `pstrNames` przy powrocie może przyjąć wartość 0, nawet jeśli funkcja zwraca `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
