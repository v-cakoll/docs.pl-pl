---
title: IMetaDataValidate::ValidatorInit — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: 687f33c364f9730a554a41ade1ca2b78e33ffdc5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489726"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="38a58-102">IMetaDataValidate::ValidatorInit — Metoda</span><span class="sxs-lookup"><span data-stu-id="38a58-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="38a58-103">Ustawia flagę określającą typ modułu w bieżącym zakresie metadanych i rejestruje określoną metodę wywołania zwrotnego dla błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="38a58-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38a58-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38a58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38a58-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="38a58-106">podczas Wartość wyliczenia [CorValidatorModuleType —](corvalidatormoduletype-enumeration.md) , która określa typ modułu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="38a58-106">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="38a58-107">podczas Wskaźnik do wystąpienia [IUnknown](/cpp/atl/iunknown) , który służy jako wywołanie zwrotne funkcji dla błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="38a58-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38a58-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38a58-108">Requirements</span></span>  
 <span data-ttu-id="38a58-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38a58-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38a58-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="38a58-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38a58-111">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38a58-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38a58-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38a58-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a58-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38a58-113">See also</span></span>

- [<span data-ttu-id="38a58-114">IMetaDataValidate — Interfejs</span><span class="sxs-lookup"><span data-stu-id="38a58-114">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)
