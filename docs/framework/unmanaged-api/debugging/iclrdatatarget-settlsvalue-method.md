---
title: ICLRDataTarget::SetTLSValue — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34c0ab32d18d5aeeb81befa736cc42b678b11fb1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738546"
---
# <a name="iclrdatatargetsettlsvalue-method"></a>ICLRDataTarget::SetTLSValue — Metoda
Ustawia wartość w pamięci lokalnej wątku (TLS) określony wątek w procesie docelowym. Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego (języka wspólnego CLR) w usłudze common language.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator systemu operacyjnego wątek w procesie docelowym.  
  
 `index`  
 [in] Indeks lokalizacji. Ta wartość musi być prawidłowy indeks w lokalnym magazynie określonego wątku.  
  
 `value`  
 [in] A `CLRDATA_ADDRESS` wartość, która określa wartości do umieszczenia w danej lokalizacji protokołu TLS.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
