---
title: "CoInitializeEE — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ca564830411a9df0d47cc9765958286bbd40f96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="coinitializeee-function"></a><span data-ttu-id="6d04b-102">CoInitializeEE — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6d04b-102">CoInitializeEE Function</span></span>
<span data-ttu-id="6d04b-103">Zapewnia, że aparat wykonywania środowiska uruchomieniowego języka wspólnego jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="6d04b-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="6d04b-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d04b-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="6d04b-105">Użyj [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="6d04b-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d04b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d04b-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d04b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d04b-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="6d04b-108">[in] Jeden z [coinitiee —](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) stałe wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6d04b-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d04b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6d04b-109">Return Value</span></span>  
 <span data-ttu-id="6d04b-110">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku Winerror.h i wartościami w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6d04b-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="6d04b-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="6d04b-111">Return code</span></span>|<span data-ttu-id="6d04b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6d04b-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6d04b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d04b-113">S_OK</span></span>|<span data-ttu-id="6d04b-114">Aparat wykonywania został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6d04b-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="6d04b-115">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6d04b-115">S_FALSE</span></span>|<span data-ttu-id="6d04b-116">Aparat wykonywania jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="6d04b-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="6d04b-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d04b-117">E_FAIL</span></span>|<span data-ttu-id="6d04b-118">Nie można załadować aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6d04b-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d04b-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d04b-119">Remarks</span></span>  
 <span data-ttu-id="6d04b-120">Ta metoda ładuje aparat wykonywania, jeśli go nie został wcześniej załadowany.</span><span class="sxs-lookup"><span data-stu-id="6d04b-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d04b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d04b-121">Requirements</span></span>  
 <span data-ttu-id="6d04b-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d04b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d04b-123">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d04b-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d04b-124">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d04b-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d04b-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d04b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d04b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d04b-126">See Also</span></span>  
 [<span data-ttu-id="6d04b-127">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="6d04b-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
