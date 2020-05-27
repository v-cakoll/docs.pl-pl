---
title: IValidator::Validate — Metoda
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 688abd210cca193bf03c40f000b74ecb66eb8ede
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008550"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="b0eda-102">IValidator::Validate — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0eda-102">IValidator::Validate Method</span></span>
<span data-ttu-id="b0eda-103">Sprawdza poprawność określonego przenośnego pliku wykonywalnego (PE) lub języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="b0eda-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0eda-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0eda-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0eda-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0eda-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="b0eda-106">podczas Wskaźnik do `IVEHandler` wystąpienia, które obsługuje błędy walidacji.</span><span class="sxs-lookup"><span data-stu-id="b0eda-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b0eda-107">podczas Wskaźnik do domeny aplikacji, w której plik zostanie załadowany.</span><span class="sxs-lookup"><span data-stu-id="b0eda-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="b0eda-108">podczas Bitowa kombinacja wartości [ValidatorFlags —](validatorflags-enumeration.md) wskazujących, które powinny być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="b0eda-108">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="b0eda-109">podczas Maksymalna liczba błędów, które należy pozostawić przed wyjściem z walidacji.</span><span class="sxs-lookup"><span data-stu-id="b0eda-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="b0eda-110">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="b0eda-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b0eda-111">podczas Ciąg określający nazwę pliku do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="b0eda-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="b0eda-112">podczas Wskaźnik do bufora pamięci, w którym przechowywany jest plik.</span><span class="sxs-lookup"><span data-stu-id="b0eda-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="b0eda-113">podczas Rozmiar pliku, który ma być zweryfikowany w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b0eda-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0eda-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0eda-114">Requirements</span></span>  
 <span data-ttu-id="b0eda-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0eda-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0eda-116">**Nagłówek:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="b0eda-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="b0eda-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b0eda-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0eda-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0eda-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
