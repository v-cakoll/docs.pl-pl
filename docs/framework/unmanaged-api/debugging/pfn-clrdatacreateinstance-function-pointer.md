---
title: PFN_CLRDataCreateInstance — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: 433f34447d3bd1a57ca1e289cb0eab3facac2c69
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790357"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance — Wskaźnik funkcji
Wskazuje funkcję, która tworzy obiekt interfejsu dla określonego elementu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
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
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)
