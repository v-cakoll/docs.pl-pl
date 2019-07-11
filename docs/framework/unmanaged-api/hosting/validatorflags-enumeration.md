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
# <a name="validatorflags-enumeration"></a><span data-ttu-id="7c326-102">ValidatorFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7c326-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="7c326-103">Zawiera wartości, które wskazują na typ sprawdzania poprawności, która powinna być wykonywana w wywołaniu [iclrvalidator::Validate —](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7c326-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c326-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c326-104">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="7c326-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7c326-105">Members</span></span>  
  
|<span data-ttu-id="7c326-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7c326-106">Member</span></span>|<span data-ttu-id="7c326-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7c326-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="7c326-108">Określa, czy mają być weryfikowane tylko języka Microsoft intermediate language (MSIL) w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="7c326-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="7c326-109">Określa, czy mają być weryfikowane tylko format pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="7c326-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="7c326-110">Określa, że wykonywane i zgłoszone wszystkich typów weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="7c326-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="7c326-111">Określa, że format pliku wykonywalnego nie powinny być weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="7c326-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="7c326-112">Określa, że komunikaty o błędach weryfikacji powinien zawierać linie kodu źródłowego, które zgłaszają błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7c326-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="7c326-113">Wartość tego pola nie jest prawidłowy w .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="7c326-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c326-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c326-114">Requirements</span></span>  
 <span data-ttu-id="7c326-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c326-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c326-116">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="7c326-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="7c326-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c326-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c326-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c326-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c326-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c326-119">See also</span></span>

- [<span data-ttu-id="7c326-120">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c326-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="7c326-121">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7c326-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
