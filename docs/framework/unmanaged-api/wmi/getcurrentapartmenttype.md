---
title: GetCurrentApartmentType, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja GetCurrentApartmentType pobiera typ mieszkania, w którym wykonuje się obiekt wywołujący.
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
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176828"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType, funkcja
Pobiera typ mieszkania, w którym wywoływany jest.
  
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
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IComThreadingInfo.](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)

`aptType`  
[na zewnątrz] Wskaźnik do wartości wyliczenia [APTTYPE,](/windows/win32/api/objidlbase/ne-objidlbase-apttype) która wskazuje mieszkanie wywołującego.

## <a name="return-value"></a>Wartość zwracana

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `S_OK` | 0 | Funkcja została ukończona pomyślnie. |
| `E_FAIL` | 0x80000008 | Dzwoniący nie wykonuje w mieszkaniu. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie metody [IComThreadingInfo::GetCurrentApartmentType.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
