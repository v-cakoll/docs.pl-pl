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
ms.openlocfilehash: 0c60631b5e034bc46d74412440d35d526359d043
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008576"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo — Metoda
Pobiera komunikat o błędzie odpowiadający określonemu błędowi walidacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Wartość HRESULT, która została przeniesiona do procedury obsługi błędów walidacji.  
  
 `Context`  
 podczas `VEContext`Wystąpienie zawierające informacje kontekstu dotyczące błędu walidacji.  
  
 `msg`  
 [in. out] Ciąg, który zawiera zwracany komunikat o błędzie.  
  
 `ulMaxLength`  
 podczas Maksymalna długość komunikatu o błędzie.  
  
 `psa`  
 podczas Bezpieczna tablica zawierająca dodatkowe parametry opisujące błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator. idl, IValidator. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
