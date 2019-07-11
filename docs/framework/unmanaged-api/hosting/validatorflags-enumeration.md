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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5f38231eb6a5911527c21ee3304fc77cfcf8e90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776521"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags — Wyliczenie
Zawiera wartości, które wskazują na typ sprawdzania poprawności, która powinna być wykonywana w wywołaniu [iclrvalidator::Validate —](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metody.  
  
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
|`VALIDATOR_CHECK_ILONLY`|Określa, czy mają być weryfikowane tylko języka Microsoft intermediate language (MSIL) w pliku wykonywalnym.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Określa, czy mają być weryfikowane tylko format pliku wykonywalnego.|  
|`VALIDATOR_EXTRA_VERBOSE`|Określa, że wykonywane i zgłoszone wszystkich typów weryfikacji.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Określa, że format pliku wykonywalnego nie powinny być weryfikowane.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Określa, że komunikaty o błędach weryfikacji powinien zawierać linie kodu źródłowego, które zgłaszają błędy sprawdzania poprawności. Wartość tego pola nie jest prawidłowy w .NET Framework w wersji 2.0.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator.idl, IValidator.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
