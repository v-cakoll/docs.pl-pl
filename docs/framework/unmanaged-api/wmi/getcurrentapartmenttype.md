---
title: GetCurrentApartmentType — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetCurrentApartmentType Pobiera typ apartamentu, w którym wykonywany jest obiekt wywołujący.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68eb4ba653098d847022da45e610cb4fa5496a8c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037963"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType, funkcja
Pobiera typ apartamentu, w którym wykonywany jest obiekt wywołujący.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .

`aptType`  
określoną Wskaźnik do [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) wartości wyliczenia, który wskazuje Apartament obiektu wywołującego.

## <a name="return-value"></a>Wartość zwracana

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `S_OK` | 0 | Funkcja została ukończona pomyślnie. |
| `E_FAIL` | 0x80000008 | Obiekt wywołujący nie jest wykonywany w apartamentie. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IComThreadingInfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
