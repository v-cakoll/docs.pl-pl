---
title: CoInitializeEE — Funkcja
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca85a12191db51818da2a08910dc9524d1ac9498
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211822"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="ff509-102">CoInitializeEE — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ff509-102">CoInitializeEE Function</span></span>
<span data-ttu-id="ff509-103">Zapewnia, że aparat wykonywania środowiska uruchomieniowego języka wspólnego jest załadowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="ff509-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="ff509-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff509-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="ff509-105">Użyj [iclrruntimehost::Start —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ff509-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff509-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff509-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff509-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff509-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="ff509-108">[in] Jedną z [coinitiee —](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) stałe wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="ff509-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff509-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ff509-109">Return Value</span></span>  
 <span data-ttu-id="ff509-110">Ta metoda zwraca standardowych kodów błędu modelu COM, zgodnie z definicją w pliku Winerror.h i wartościami w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ff509-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="ff509-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="ff509-111">Return code</span></span>|<span data-ttu-id="ff509-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ff509-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ff509-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff509-113">S_OK</span></span>|<span data-ttu-id="ff509-114">Aparat wykonywania został pomyślnie załadowany.</span><span class="sxs-lookup"><span data-stu-id="ff509-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="ff509-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ff509-115">S_FALSE</span></span>|<span data-ttu-id="ff509-116">Aparat wykonywania jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="ff509-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="ff509-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ff509-117">E_FAIL</span></span>|<span data-ttu-id="ff509-118">Nie można załadować aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ff509-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff509-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff509-119">Remarks</span></span>  
 <span data-ttu-id="ff509-120">Ta metoda ładuje aparatu wykonywania, jeśli nie został wcześniej załadowany.</span><span class="sxs-lookup"><span data-stu-id="ff509-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff509-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff509-121">Requirements</span></span>  
 <span data-ttu-id="ff509-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff509-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff509-123">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ff509-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff509-124">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff509-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff509-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff509-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff509-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff509-126">See also</span></span>
- [<span data-ttu-id="ff509-127">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="ff509-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
