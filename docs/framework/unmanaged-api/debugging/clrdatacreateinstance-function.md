---
title: CLRDataCreateInstance — Funkcja
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: 71836108dbd0ce01a64b4d9ac773c28d385dfd7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099689"
---
# <a name="clrdatacreateinstance-function"></a>CLRDataCreateInstance — Funkcja
Tworzy obiekt interfejsu dla określonego elementu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iid`  
 podczas Identyfikator interfejsu, który ma zostać utworzony.  
  
 `target`  
 podczas Wskaźnik do obiektu [ICLRDataTarget](iclrdatatarget-interface.md) zaimplementowanego przez użytkownika, który reprezentuje element docelowy, dla którego ma zostać utworzony obiekt interfejsu.  
  
 `iface`  
 określoną Wskaźnik do adresu zwróconego obiektu interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `ICLRDataTarget` jest implementowany przez moduł zapisujący aplikacji debugowania. Implementacja zależy od typu reprezentowanego elementu docelowego. Element docelowy może być procesem, zrzutem pamięci, maszyną zdalną i tak dalej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)
