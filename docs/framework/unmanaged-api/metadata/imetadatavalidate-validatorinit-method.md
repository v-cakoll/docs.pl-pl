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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31ff2c62810061cd8b774e934167a5ee3acf040c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645090"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="1b105-102">IMetaDataValidate::ValidatorInit — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b105-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="1b105-103">Ustawia flagę, która określa typ modułu w bieżącym zakresie metadanych i rejestruje metodą określonego wywołania zwrotnego dla błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="1b105-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b105-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b105-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b105-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b105-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="1b105-106">[in] Wartość [corvalidatormoduletype —](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) wyliczenie, który określa typ modułu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="1b105-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="1b105-107">[in] Wskaźnik do [IUnknown](/cpp/atl/iunknown) wystąpienia, która służy jako funkcja wywołania zwrotnego dla błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="1b105-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b105-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b105-108">Requirements</span></span>  
 <span data-ttu-id="1b105-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b105-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b105-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1b105-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b105-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b105-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b105-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b105-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b105-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b105-113">See also</span></span>

- [<span data-ttu-id="1b105-114">IMetaDataValidate, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b105-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
