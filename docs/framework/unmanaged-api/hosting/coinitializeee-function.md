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
ms.openlocfilehash: 9e90772ae8c3e6be5744fcccc9901123df871831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131941"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="48fd6-102">CoInitializeEE — Funkcja</span><span class="sxs-lookup"><span data-stu-id="48fd6-102">CoInitializeEE Function</span></span>
<span data-ttu-id="48fd6-103">Zapewnia, że aparat wykonywania środowiska uruchomieniowego języka wspólnego jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="48fd6-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="48fd6-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="48fd6-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="48fd6-105">Zamiast tego użyj metody [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="48fd6-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48fd6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="48fd6-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48fd6-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="48fd6-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="48fd6-108">podczas Jedna ze stałych wyliczenia [COINITIEE —](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="48fd6-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48fd6-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="48fd6-109">Return Value</span></span>  
 <span data-ttu-id="48fd6-110">Ta metoda zwraca standardowe kody błędów COM zdefiniowane w Winerror. h i wartości w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="48fd6-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="48fd6-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="48fd6-111">Return code</span></span>|<span data-ttu-id="48fd6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="48fd6-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="48fd6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="48fd6-113">S_OK</span></span>|<span data-ttu-id="48fd6-114">Aparat wykonywania został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="48fd6-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="48fd6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="48fd6-115">S_FALSE</span></span>|<span data-ttu-id="48fd6-116">Aparat wykonywania został już załadowany.</span><span class="sxs-lookup"><span data-stu-id="48fd6-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="48fd6-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48fd6-117">E_FAIL</span></span>|<span data-ttu-id="48fd6-118">Nie można załadować aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="48fd6-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48fd6-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48fd6-119">Remarks</span></span>  
 <span data-ttu-id="48fd6-120">Ta metoda ładuje aparat wykonywania, jeśli nie został wcześniej załadowany.</span><span class="sxs-lookup"><span data-stu-id="48fd6-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48fd6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48fd6-121">Requirements</span></span>  
 <span data-ttu-id="48fd6-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48fd6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48fd6-123">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="48fd6-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48fd6-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48fd6-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48fd6-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48fd6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48fd6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48fd6-126">See also</span></span>

- [<span data-ttu-id="48fd6-127">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="48fd6-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
