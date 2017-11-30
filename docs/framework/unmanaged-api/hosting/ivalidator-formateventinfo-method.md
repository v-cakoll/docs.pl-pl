---
title: "IValidator::FormatEventInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0775bf5a2370d9d05899af5bc414caf08b3401fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo — Metoda
Pobiera odpowiadający błąd sprawdzania poprawności określony komunikat o błędzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hVECode`  
 [in] Wartość HRESULT, która została przekazana do obsługi błędów sprawdzania poprawności.  
  
 `Context`  
 [in] A `VEContext` wystąpienia, które zawiera informacje o kontekście o błędzie sprawdzania poprawności.  
  
 `msg`  
 [w, out] Ciąg, który zawiera komunikat zwrócony kod błędu.  
  
 `ulMaxLength`  
 [in] Maksymalna długość komunikatu o błędzie.  
  
 `psa`  
 [in] Bezpieczne tablica, która zawiera dodatkowe parametry opisujące błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator.idl, IValidator.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
