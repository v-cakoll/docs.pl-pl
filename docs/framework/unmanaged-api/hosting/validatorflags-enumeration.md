---
title: ValidatorFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
ms.openlocfilehash: 61aafb8dc99bb908fc603945ff6ea74054f812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141420"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags — Wyliczenie
Zawiera wartości wskazujące typ walidacji, który powinien zostać wykonany w wywołaniu metody [ICLRValidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|Określa, że należy sprawdzić poprawność tylko języka pośredniego firmy Microsoft (MSIL) w pliku wykonywalnym.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Określa, że należy zweryfikować tylko format pliku wykonywalnego.|  
|`VALIDATOR_EXTRA_VERBOSE`|Określa, że wszystkie typy walidacji powinny być wykonywane i raportowane na.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Określa, że format pliku wykonywalnego nie powinien być zweryfikowany.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Określa, że komunikaty o błędach weryfikacji powinny zawierać wiersze kodu źródłowego, które powodują błędy walidacji. Ta wartość pola jest nieprawidłowa w .NET Framework w wersji 2,0.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator. idl, IValidator. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
