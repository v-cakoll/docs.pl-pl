---
title: INotifyConnection2::RegisterNotifySource — Metoda
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: b7fa777466e2c7edd7b3110dd91e776785c63c58
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442075"
---
# <a name="inotifyconnection2registernotifysource-method"></a>INotifyConnection2::RegisterNotifySource — Metoda
Instaluje określone źródło powiadomień.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_pNotifySource`  
 podczas Określa obiekt, który ma być używany jako źródło powiadomienia.  
  
 `out_ppNotifySink`  
 określoną Odbiera obiekt, który ma być używany jako ujścia powiadomień.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Zobacz także

- [INotifyConnection2 — Interfejs](inotifyconnection2-interface.md)
- [INotifySource2 — Interfejs](inotifysource2-interface.md)
- [INotifySink2 — Interfejs](inotifysink2-interface.md)
- [UnregisterNotifySource, metoda](inotifyconnection2-unregisternotifysource-method.md)
