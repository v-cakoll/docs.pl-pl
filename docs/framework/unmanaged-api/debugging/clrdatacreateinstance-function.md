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
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179360"
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
 [w] Identyfikator interfejsu, który ma zostać skreślony.  
  
 `target`  
 [w] Wskaźnik do obiektu [ICLRDataTarget](iclrdatatarget-interface.md) zaimplementowanego przez użytkownika, który reprezentuje element docelowy, dla którego ma zostać utworzony obiekt interfejsu.  
  
 `iface`  
 [na zewnątrz] Wskaźnik do adresu zwracanego obiektu interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `ICLRDataTarget` jest implementowany przez moduł zapisujący aplikacji debugowania. Implementacja zależy od typu elementu docelowego reprezentowanego. Element docelowy może być procesem, zrzutem pamięci, komputerem zdalnym i tak dalej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Plik ClrData.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)
