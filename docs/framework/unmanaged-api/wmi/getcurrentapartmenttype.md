---
title: Funkcja GetCurrentApartmentType (niezarządzany wykaz interfejsów API)
description: Funkcja GetCurrentApartmentType pobiera typu apartment, w którym jest wykonywany obiekt wywołujący.
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
ms.openlocfilehash: 8a999dc1850a41612f8896ff9a7ed96cd8c3a2fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509138"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType — funkcja
Pobiera rodzaj typu apartment, w którym jest wykonywany obiekt wywołujący.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) wystąpienia.

`aptType`  
[out] Wskaźnik do [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) wartość wyliczenia wskazująca apartamentu obiektu wywołującego.

## <a name="return-value"></a>Wartość zwracana


|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `S_OK` | 0 | Funkcja została ukończona pomyślnie. |
| `E_FAIL` | 0x80000008 | Obiekt wywołujący nie jest wykonywana w komórce. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
