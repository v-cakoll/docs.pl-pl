---
title: "ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda"
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
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf6860a616312504e3d23177734cb532405bd714
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="3d6bd-102">ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d6bd-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>
<span data-ttu-id="3d6bd-103">Pobiera dostawcę biblioteki interfejsu wywołania zwrotnego, który umożliwia wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) określonej wersji biblioteki debugowania należy odnaleźć i załadować na żądanie.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d6bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d6bd-104">Syntax</span></span>  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d6bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d6bd-105">Parameters</span></span>  
 `pwszFilename`  
 <span data-ttu-id="3d6bd-106">[in] Nazwa modułu żądanej.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-106">[in] The name of the module being requested .</span></span>  
  
 `dwTimestamp`  
 <span data-ttu-id="3d6bd-107">[in] Sygnatury czasowej przechowywane w nagłówku pliku PE — pliki COFF.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="3d6bd-108">[in] `SizeOfImage` Pola przechowywane w nagłówku COFF opcjonalny plik PE — pliki.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>  
  
 `hModule`  
 <span data-ttu-id="3d6bd-109">[out] Dojście do żądanego modułu.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-109">[out] The handle to the requested module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d6bd-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3d6bd-110">Return Value</span></span>  
 <span data-ttu-id="3d6bd-111">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3d6bd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d6bd-112">HRESULT</span></span>|<span data-ttu-id="3d6bd-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3d6bd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d6bd-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d6bd-114">S_OK</span></span>|<span data-ttu-id="3d6bd-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-115">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="3d6bd-116">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="3d6bd-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d6bd-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d6bd-117">Remarks</span></span>  
 <span data-ttu-id="3d6bd-118">`ProvideLibrary`Umożliwia debugera zapewnić modułów, które są wymagane do debugowania określonych plików CLR, takie jak mscordbi.dll i pliku mscordacwks.dll.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="3d6bd-119">Uchwyty modułu muszą być prawidłowe do wywołania [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) metody wskazuje, że mogą one zostać zwolniony w takim przypadku odpowiada wywołującego wolne uchwytów.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>  
  
 <span data-ttu-id="3d6bd-120">Debuger może używać oznacza, że wszystkie dostępne do zlokalizowania lub uzyskaj moduł debugowania.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-120">The debugger may use any available means to locate or procure the debugging module.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d6bd-121">Ta funkcja umożliwia wywołującego interfejs API zapewnić modułów zawierających pliku wykonywalnego i potencjalnie złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="3d6bd-122">Ze względów bezpieczeństwa nie należy używać wywołującego `ProvideLibrary` do dystrybucji dowolny kod, że nie jest gotowa do wykonania sam.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>  
>   
>  <span data-ttu-id="3d6bd-123">Jeśli poważny problem został odnaleziony w bibliotece już zwolnione, takie jak mscordbi.dll lub pliku mscordacwks.dll, podkładki można serwisować rozpoznawanie zły wersje plików.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="3d6bd-124">Podkładka może, a następnie wysyłania żądań do poprawioną wersje plików i odrzucić zły wersji, jeśli są one udostępniane w odpowiedzi na każde żądanie.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="3d6bd-125">To może występować tylko wtedy, gdy użytkownik ma poprawiono do nowej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="3d6bd-126">Które wersje pozostanie zagrożone.</span><span class="sxs-lookup"><span data-stu-id="3d6bd-126">Unpatched versions will remain vulnerable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d6bd-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d6bd-127">Requirements</span></span>  
 <span data-ttu-id="3d6bd-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d6bd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d6bd-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d6bd-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d6bd-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d6bd-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d6bd-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d6bd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6bd-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d6bd-132">See Also</span></span>  
 [<span data-ttu-id="3d6bd-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3d6bd-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3d6bd-134">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3d6bd-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
