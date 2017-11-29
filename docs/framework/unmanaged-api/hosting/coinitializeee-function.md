---
title: "CoInitializeEE — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoInitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoInitializeEE
helpviewer_keywords: CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 429d055ec0853d04f794b063a76a395d98aceb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="coinitializeee-function"></a><span data-ttu-id="ddcf9-102">CoInitializeEE — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ddcf9-102">CoInitializeEE Function</span></span>
<span data-ttu-id="ddcf9-103">Zapewnia, że aparat wykonywania środowiska uruchomieniowego języka wspólnego jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="ddcf9-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="ddcf9-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ddcf9-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="ddcf9-105">Użyj [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ddcf9-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcf9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddcf9-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddcf9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddcf9-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="ddcf9-108">[in] Jeden z [coinitiee —](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) stałe wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ddcf9-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddcf9-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ddcf9-109">Return Value</span></span>  
 <span data-ttu-id="ddcf9-110">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku Winerror.h i wartościami w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ddcf9-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="ddcf9-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="ddcf9-111">Return code</span></span>|<span data-ttu-id="ddcf9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ddcf9-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ddcf9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ddcf9-113">S_OK</span></span>|<span data-ttu-id="ddcf9-114">Aparat wykonywania został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ddcf9-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="ddcf9-115">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ddcf9-115">S_FALSE</span></span>|<span data-ttu-id="ddcf9-116">Aparat wykonywania jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="ddcf9-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="ddcf9-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ddcf9-117">E_FAIL</span></span>|<span data-ttu-id="ddcf9-118">Nie można załadować aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ddcf9-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddcf9-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddcf9-119">Remarks</span></span>  
 <span data-ttu-id="ddcf9-120">Ta metoda ładuje aparat wykonywania, jeśli go nie został wcześniej załadowany.</span><span class="sxs-lookup"><span data-stu-id="ddcf9-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddcf9-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddcf9-121">Requirements</span></span>  
 <span data-ttu-id="ddcf9-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddcf9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddcf9-123">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ddcf9-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddcf9-124">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ddcf9-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ddcf9-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcf9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcf9-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddcf9-126">See Also</span></span>  
 [<span data-ttu-id="ddcf9-127">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="ddcf9-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
