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
ms.openlocfilehash: a1b02bb74a61e64a3ed9875fcf88e018de9f6317
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041442"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="27dab-102">ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda</span><span class="sxs-lookup"><span data-stu-id="27dab-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="27dab-103">Pobiera interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego języka wspólnego (CLR) na żądanie.</span><span class="sxs-lookup"><span data-stu-id="27dab-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="27dab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27dab-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="27dab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27dab-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="27dab-106">podczas Nazwa żądanego modułu.</span><span class="sxs-lookup"><span data-stu-id="27dab-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="27dab-107">podczas Sygnatura czasowa, która jest przechowywana w nagłówku pliku COFF plików PE.</span><span class="sxs-lookup"><span data-stu-id="27dab-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="27dab-108">podczas `SizeOfImage` Pole przechowywane w nagłówku opcjonalnego pliku w formacie COFF.</span><span class="sxs-lookup"><span data-stu-id="27dab-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="27dab-109">określoną Uchwyt do żądanego modułu.</span><span class="sxs-lookup"><span data-stu-id="27dab-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="27dab-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="27dab-110">Return Value</span></span>

<span data-ttu-id="27dab-111">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="27dab-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="27dab-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27dab-112">HRESULT</span></span>|<span data-ttu-id="27dab-113">Opis</span><span class="sxs-lookup"><span data-stu-id="27dab-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="27dab-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="27dab-114">S_OK</span></span>|<span data-ttu-id="27dab-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="27dab-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="27dab-116">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="27dab-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="27dab-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27dab-117">Remarks</span></span>

<span data-ttu-id="27dab-118">`ProvideLibrary`umożliwia debugerowi dostarczanie modułów, które są konieczne do debugowania określonych plików CLR, takich jak mscordbi. dll i mscordacwks. dll.</span><span class="sxs-lookup"><span data-stu-id="27dab-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="27dab-119">Obsługa modułów musi pozostać ważna, dopóki wywołanie metody [ICLRDebugging:: CanUnloadNow —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) nie wskazuje, że mogą być zwolnione, a tym samym jest odpowiedzialnością wywołującą, aby zwolnić dojścia.</span><span class="sxs-lookup"><span data-stu-id="27dab-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="27dab-120">Debuger może używać dowolnego dostępnego środka do lokalizowania lub pozyskiwania modułu debugowania.</span><span class="sxs-lookup"><span data-stu-id="27dab-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27dab-121">Ta funkcja umożliwia obiektowi wywołującemu interfejsu API dostarczanie modułów, które zawierają plik wykonywalny, i prawdopodobnie złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="27dab-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="27dab-122">Ze względów bezpieczeństwa, wywołujący nie powinien używać `ProvideLibrary` do dystrybuowania żadnego kodu, który nie jest gotowy do wykonania.</span><span class="sxs-lookup"><span data-stu-id="27dab-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="27dab-123">W przypadku odnalezienia poważnego problemu z zabezpieczeniami w już wydanej bibliotece, takiej jak mscordbi. dll lub mscordacwks. dll, Poprawka podkładki może zostać poprawiona w celu rozpoznania nieprawidłowych wersji plików.</span><span class="sxs-lookup"><span data-stu-id="27dab-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="27dab-124">Podkładka może następnie wydać żądania dotyczące wersji plików z poprawkami i odrzucić niewłaściwe wersje, jeśli są one dostarczane w odpowiedzi na jakiekolwiek żądanie.</span><span class="sxs-lookup"><span data-stu-id="27dab-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="27dab-125">Taka sytuacja może wystąpić tylko wtedy, gdy użytkownik połączył się z nową wersją podkładki.</span><span class="sxs-lookup"><span data-stu-id="27dab-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="27dab-126">Niepoprawione wersje pozostaną zagrożone.</span><span class="sxs-lookup"><span data-stu-id="27dab-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="27dab-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27dab-127">Requirements</span></span>

<span data-ttu-id="27dab-128">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27dab-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="27dab-129">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27dab-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="27dab-130">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27dab-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="27dab-131">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27dab-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="27dab-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27dab-132">See also</span></span>

- [<span data-ttu-id="27dab-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="27dab-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="27dab-134">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="27dab-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
