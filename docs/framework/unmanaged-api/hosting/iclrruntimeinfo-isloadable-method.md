---
title: ICLRRuntimeInfo::IsLoadable — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: a1cd169fc4be5b1dd3ab1a83f4ad143ba2e2442b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007367"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="fb60c-102">ICLRRuntimeInfo::IsLoadable — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb60c-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="fb60c-103">Wskazuje, czy środowisko uruchomieniowe skojarzone z tym interfejsem może zostać załadowane do bieżącego procesu, biorąc pod uwagę inne środowiska uruchomieniowe, które mogły już zostać załadowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="fb60c-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb60c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb60c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb60c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb60c-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="fb60c-106">[out] `true` Jeśli to środowisko uruchomieniowe może zostać załadowane do bieżącego procesu; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="fb60c-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb60c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fb60c-107">Return Value</span></span>  
 <span data-ttu-id="fb60c-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="fb60c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fb60c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb60c-109">HRESULT</span></span>|<span data-ttu-id="fb60c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fb60c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb60c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb60c-111">S_OK</span></span>|<span data-ttu-id="fb60c-112">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fb60c-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="fb60c-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fb60c-113">E_POINTER</span></span>|<span data-ttu-id="fb60c-114">`pbLoadable`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="fb60c-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb60c-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb60c-115">Remarks</span></span>  
 <span data-ttu-id="fb60c-116">Jeśli inne środowisko uruchomieniowe jest już załadowane do procesu, a środowisko uruchomieniowe skojarzone z tym interfejsem może zostać załadowane do wykonywania równoczesnego, `pbLoadable` zwraca wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="fb60c-116">If another runtime is already loaded into the process, and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="fb60c-117">Jeśli dwa środowiska uruchomieniowe nie mogą być uruchamiane równolegle, `pbLoadable` Funkcja zwraca wartość `false` .</span><span class="sxs-lookup"><span data-stu-id="fb60c-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="fb60c-118">Na przykład środowisko uruchomieniowe języka wspólnego (CLR) w wersji 4 może działać obok siebie w tym samym procesie, przy użyciu środowiska CLR w wersji 2,0 lub CLR w wersji 1,1.</span><span class="sxs-lookup"><span data-stu-id="fb60c-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="fb60c-119">Jednak środowisko CLR w wersji 1,1 i środowisko CLR w wersji 2,0 nie mogą być uruchamiane równolegle.</span><span class="sxs-lookup"><span data-stu-id="fb60c-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="fb60c-120">Jeśli żadne środowisko uruchomieniowe nie zostanie załadowane do procesu, ta metoda zawsze zwraca wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="fb60c-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb60c-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb60c-121">Requirements</span></span>  
 <span data-ttu-id="fb60c-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb60c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb60c-123">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="fb60c-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fb60c-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fb60c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb60c-125">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb60c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb60c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb60c-126">See also</span></span>

- [<span data-ttu-id="fb60c-127">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb60c-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="fb60c-128">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fb60c-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="fb60c-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="fb60c-129">Hosting</span></span>](index.md)
