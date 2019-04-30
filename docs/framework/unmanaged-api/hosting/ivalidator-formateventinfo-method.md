---
title: IValidator::FormatEventInfo — Metoda
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecbecec86d81357000679ab50e12f06d91c9f50d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765378"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo — Metoda
Pobiera komunikat o błędzie odpowiadający błąd sprawdzania poprawności określonej.  
  
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
  
## <a name="parameters"></a>Parametry  
 `hVECode`  
 [in] Wartość HRESULT, który został przekazany do procedury obsługi błędów sprawdzania poprawności.  
  
 `Context`  
 [in] A `VEContext` wystąpienia, które zawiera informacje o kontekście o błędzie sprawdzania poprawności.  
  
 `msg`  
 [out w] Ciąg, który zawiera komunikat zwrócony kod błędu.  
  
 `ulMaxLength`  
 [in] Maksymalna długość komunikatu o błędzie.  
  
 `psa`  
 [in] Bezpieczne tablicę, która zawiera dodatkowe parametry opisujące błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator.idl, IValidator.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
