---
title: ICLRRuntimeInfo::LoadLibrary — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 09c80c3a56d86943ebe00e5222bb5452ab44e150
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762178"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="6b137-102">ICLRRuntimeInfo::LoadLibrary — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b137-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="6b137-103">Ładuje bibliotekę .NET Framework z aparatu plików wykonywalnych języka wspólnego (CLR) reprezentowanego przez interfejs [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6b137-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="6b137-104">Ta metoda zastępuje funkcję [LoadLibraryShim —](loadlibraryshim-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6b137-104">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b137-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b137-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b137-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b137-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="6b137-107">podczas Nazwa zestawu, który ma zostać załadowany.</span><span class="sxs-lookup"><span data-stu-id="6b137-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="6b137-108">określoną Dojście do ładowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="6b137-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b137-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b137-109">Return Value</span></span>  
 <span data-ttu-id="6b137-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="6b137-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6b137-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b137-111">HRESULT</span></span>|<span data-ttu-id="6b137-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6b137-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b137-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b137-113">S_OK</span></span>|<span data-ttu-id="6b137-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b137-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6b137-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6b137-115">E_POINTER</span></span>|<span data-ttu-id="6b137-116">`pwzDllName`lub `phndModule` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="6b137-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="6b137-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6b137-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6b137-118">Za mało dostępnej pamięci, aby obsłużyć żądanie.</span><span class="sxs-lookup"><span data-stu-id="6b137-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b137-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b137-119">Remarks</span></span>  
 <span data-ttu-id="6b137-120">Ta metoda ładuje tylko biblioteki dll zawarte w pakiecie redystrybucyjnym .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b137-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="6b137-121">Nie można załadować zestawów wygenerowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6b137-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b137-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b137-122">Requirements</span></span>  
 <span data-ttu-id="6b137-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b137-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b137-124">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="6b137-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6b137-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6b137-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b137-126">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b137-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b137-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b137-127">See also</span></span>

- [<span data-ttu-id="6b137-128">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b137-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6b137-129">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6b137-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6b137-130">Hosting</span><span class="sxs-lookup"><span data-stu-id="6b137-130">Hosting</span></span>](index.md)
