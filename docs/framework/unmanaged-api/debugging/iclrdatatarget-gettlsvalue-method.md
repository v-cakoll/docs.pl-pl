---
title: ICLRDataTarget::GetTLSValue — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: d4e7c055480ea611357d5d3e18ac4306acf4d0b0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785415"
---
# <a name="iclrdatatargetgettlsvalue-method"></a>ICLRDataTarget::GetTLSValue — Metoda
Pobiera wartość z lokalnego magazynu wątków (TLS) określonego wątku w procesie docelowym. Ta metoda jest wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 podczas Identyfikator systemu operacyjnego wątku w procesie docelowym.  
  
 `index`  
 podczas Indeks lokalizacji. Ta wartość musi być prawidłowym indeksem w magazynie lokalnym określonego wątku.  
  
 `value`  
 określoną Wskaźnik do wartości `CLRDATA_ADDRESS`, która określa wartość zwracaną z danej lokalizacji protokołu TLS.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](iclrdatatarget-interface.md)
