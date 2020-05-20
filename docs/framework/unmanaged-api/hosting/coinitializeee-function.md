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
ms.openlocfilehash: 57508a2df3a49c39d25347f2a3038442c37278da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616765"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="2b559-102">CoInitializeEE — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2b559-102">CoInitializeEE Function</span></span>
<span data-ttu-id="2b559-103">Zapewnia, że aparat wykonywania środowiska uruchomieniowego języka wspólnego jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="2b559-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="2b559-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2b559-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="2b559-105">Zamiast tego użyj metody [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2b559-105">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b559-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b559-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b559-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b559-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="2b559-108">podczas Jedna ze stałych wyliczenia [COINITIEE —](../metadata/coinitiee-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="2b559-108">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b559-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b559-109">Return Value</span></span>  
 <span data-ttu-id="2b559-110">Ta metoda zwraca standardowe kody błędów COM zdefiniowane w Winerror. h i wartości w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2b559-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="2b559-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="2b559-111">Return code</span></span>|<span data-ttu-id="2b559-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2b559-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2b559-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b559-113">S_OK</span></span>|<span data-ttu-id="2b559-114">Aparat wykonywania został załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2b559-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="2b559-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2b559-115">S_FALSE</span></span>|<span data-ttu-id="2b559-116">Aparat wykonywania został już załadowany.</span><span class="sxs-lookup"><span data-stu-id="2b559-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="2b559-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b559-117">E_FAIL</span></span>|<span data-ttu-id="2b559-118">Nie można załadować aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2b559-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b559-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b559-119">Remarks</span></span>  
 <span data-ttu-id="2b559-120">Ta metoda ładuje aparat wykonywania, jeśli nie został wcześniej załadowany.</span><span class="sxs-lookup"><span data-stu-id="2b559-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b559-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b559-121">Requirements</span></span>  
 <span data-ttu-id="2b559-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b559-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b559-123">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2b559-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b559-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2b559-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b559-125">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b559-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b559-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b559-126">See also</span></span>

- [<span data-ttu-id="2b559-127">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="2b559-127">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
