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
ms.openlocfilehash: d5eb225241f597baf7a0a5584f4aaf8bf8411ea2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009473"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="3a22d-102">ValidatorFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3a22d-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="3a22d-103">Zawiera wartości wskazujące typ walidacji, który powinien zostać wykonany w wywołaniu metody [ICLRValidator:: Validate](iclrvalidator-validate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3a22d-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a22d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a22d-104">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="3a22d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3a22d-105">Members</span></span>  
  
|<span data-ttu-id="3a22d-106">Członek</span><span class="sxs-lookup"><span data-stu-id="3a22d-106">Member</span></span>|<span data-ttu-id="3a22d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3a22d-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="3a22d-108">Określa, że należy sprawdzić poprawność tylko języka pośredniego firmy Microsoft (MSIL) w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="3a22d-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="3a22d-109">Określa, że należy zweryfikować tylko format pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="3a22d-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="3a22d-110">Określa, że wszystkie typy walidacji powinny być wykonywane i raportowane na.</span><span class="sxs-lookup"><span data-stu-id="3a22d-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="3a22d-111">Określa, że format pliku wykonywalnego nie powinien być zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="3a22d-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="3a22d-112">Określa, że komunikaty o błędach weryfikacji powinny zawierać wiersze kodu źródłowego, które powodują błędy walidacji.</span><span class="sxs-lookup"><span data-stu-id="3a22d-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="3a22d-113">Ta wartość pola jest nieprawidłowa w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="3a22d-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a22d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a22d-114">Requirements</span></span>  
 <span data-ttu-id="3a22d-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a22d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a22d-116">**Nagłówek:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="3a22d-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="3a22d-117">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3a22d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a22d-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a22d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a22d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a22d-119">See also</span></span>

- [<span data-ttu-id="3a22d-120">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a22d-120">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="3a22d-121">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3a22d-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
