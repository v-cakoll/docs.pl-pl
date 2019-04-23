---
title: ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f5d44b6497e971e6d1ed030c043b91b88c070b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218514"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="90e91-102">ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda</span><span class="sxs-lookup"><span data-stu-id="90e91-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>
<span data-ttu-id="90e91-103">Pobiera dostawcę biblioteki interfejs wywołania zwrotnego, która umożliwia bibliotekom debudowania określonych wersji środowiska uruchomieniowego (języka wspólnego CLR) lokalizowanie i ładowanie na żądanie języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="90e91-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90e91-104">Syntax</span></span>  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90e91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90e91-105">Parameters</span></span>  
 `pwszFilename`  
 <span data-ttu-id="90e91-106">[in] Nazwa modułu żądanej.</span><span class="sxs-lookup"><span data-stu-id="90e91-106">[in] The name of the module being requested.</span></span>  
  
 `dwTimestamp`  
 <span data-ttu-id="90e91-107">[in] Sygnatura czasowa daty zapisane w nagłówku pliku COFF plików PE.</span><span class="sxs-lookup"><span data-stu-id="90e91-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="90e91-108">[in] `SizeOfImage` Pola przechowywane w nagłówku pliku opcjonalne COFF plików PE.</span><span class="sxs-lookup"><span data-stu-id="90e91-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>  
  
 `hModule`  
 <span data-ttu-id="90e91-109">[out] Dojście do żądanego modułu.</span><span class="sxs-lookup"><span data-stu-id="90e91-109">[out] The handle to the requested module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90e91-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="90e91-110">Return Value</span></span>  
 <span data-ttu-id="90e91-111">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="90e91-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90e91-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90e91-112">HRESULT</span></span>|<span data-ttu-id="90e91-113">Opis</span><span class="sxs-lookup"><span data-stu-id="90e91-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90e91-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="90e91-114">S_OK</span></span>|<span data-ttu-id="90e91-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="90e91-115">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="90e91-116">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="90e91-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90e91-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90e91-117">Remarks</span></span>  
 <span data-ttu-id="90e91-118">`ProvideLibrary` Umożliwia debugera, aby zapewnić moduły, które są wymagane do debugowania określone pliki CLR, takich jak plik mscordbi.dll i pliku mscordacwks.dll.</span><span class="sxs-lookup"><span data-stu-id="90e91-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="90e91-119">Uchwyty modułu trzeba pozostaje ważne do wywołania [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) metoda wskazuje, że mogą one być zwolniona, w tym momencie jest obiekt wywołujący odpowiada za zwolnienie uchwyty.</span><span class="sxs-lookup"><span data-stu-id="90e91-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>  
  
 <span data-ttu-id="90e91-120">Debuger może zlokalizować lub uzyskać moduł debugowania za pomocą dowolnej metody dostępne.</span><span class="sxs-lookup"><span data-stu-id="90e91-120">The debugger may use any available means to locate or procure the debugging module.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90e91-121">Ta funkcja umożliwia wywołującego interfejs API zapewnić modułów zawierających pliku wykonywalnego i potencjalnie złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="90e91-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="90e91-122">Ze względów bezpieczeństwa nie należy używać obiekt wywołujący `ProvideLibrary` do dystrybucji jakiegokolwiek kodu, że nie jest gotowa do wykonania samej.</span><span class="sxs-lookup"><span data-stu-id="90e91-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>  
>   
>  <span data-ttu-id="90e91-123">Jeśli problem z powodu poważnego naruszenia zabezpieczeń został odnaleziony w bibliotece już zwolnione, takich jak plik mscordbi.dll lub pliku, w tym mscordacwks.dll podkładka poprawkę można zastosować do rozpoznawania nieprawidłowe wersje plików.</span><span class="sxs-lookup"><span data-stu-id="90e91-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="90e91-124">Podkładka można, a następnie wysyłać żądania dotyczące poprawionego wersji plików i Odrzuć nieprawidłowe wersje, jeśli są one udostępniane w odpowiedzi na każde żądanie.</span><span class="sxs-lookup"><span data-stu-id="90e91-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="90e91-125">To może wystąpić tylko wtedy, gdy użytkownik ma zastosować poprawki do nowej wersji podkładka.</span><span class="sxs-lookup"><span data-stu-id="90e91-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="90e91-126">Które wersje będą nadal są narażone.</span><span class="sxs-lookup"><span data-stu-id="90e91-126">Unpatched versions will remain vulnerable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90e91-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90e91-127">Requirements</span></span>  
 <span data-ttu-id="90e91-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90e91-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90e91-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90e91-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90e91-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90e91-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90e91-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90e91-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e91-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90e91-132">See also</span></span>

- [<span data-ttu-id="90e91-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="90e91-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="90e91-134">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="90e91-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
