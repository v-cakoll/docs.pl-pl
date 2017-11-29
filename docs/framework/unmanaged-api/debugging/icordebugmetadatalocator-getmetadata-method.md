---
title: "ICorDebugMetaDataLocator::GetMetaData — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMetaDataLocator.GetMetaData
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42c0548a626d43592184efa92619e74446058d58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="31db4-102">ICorDebugMetaDataLocator::GetMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="31db4-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="31db4-103">Pyta debugera do zwrócenia pełną ścieżkę do modułu, którego metadanych wymaganego do ukończenia operacji żądanej przez debuger.</span><span class="sxs-lookup"><span data-stu-id="31db4-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31db4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31db4-104">Syntax</span></span>  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31db4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31db4-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="31db4-106">[in] Ciąg zerem, który reprezentuje pełną ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="31db4-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="31db4-107">Jeśli pełna ścieżka nie jest dostępna, nazwę i rozszerzenie pliku (*filename*. *rozszerzenie*).</span><span class="sxs-lookup"><span data-stu-id="31db4-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="31db4-108">[in] Sygnatura czasowa z nagłówków pliku PE obrazu.</span><span class="sxs-lookup"><span data-stu-id="31db4-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="31db4-109">Ten parametr potencjalnie może służyć do serwera symboli ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="31db4-109">This parameter can potentially be used for a symbol server ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="31db4-110">[in] Rozmiar obrazu z nagłówków pliku PE.</span><span class="sxs-lookup"><span data-stu-id="31db4-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="31db4-111">Ten parametr potencjalnie może służyć do wyszukiwania SymSrv.</span><span class="sxs-lookup"><span data-stu-id="31db4-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="31db4-112">[in] Liczba znaków `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="31db4-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="31db4-113">[out] Liczba `WCHAR`s zapisane `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="31db4-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="31db4-114">Jeśli metoda zwraca E_NOT_SUFFICIENT_BUFFER, zawiera liczbę `WCHAR`s niezbędne do przechowywania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="31db4-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="31db4-115">[out] Wskaźnik do buforu, w której debuger skopiuje pełną ścieżkę pliku, który zawiera żądanych metadanych.</span><span class="sxs-lookup"><span data-stu-id="31db4-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="31db4-116">`ofReadOnly` Flaga z [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczenie jest używane do żądania dostępu tylko do odczytu do metadanych w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="31db4-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31db4-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="31db4-117">Return Value</span></span>  
 <span data-ttu-id="31db4-118">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="31db4-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="31db4-119">Wszystkich innych wyników HRESULT awarii wskazują, że plik nie jest pobieranie.</span><span class="sxs-lookup"><span data-stu-id="31db4-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="31db4-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31db4-120">HRESULT</span></span>|<span data-ttu-id="31db4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="31db4-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31db4-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="31db4-122">S_OK</span></span>|<span data-ttu-id="31db4-123">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="31db4-123">The method completed successfully.</span></span> <span data-ttu-id="31db4-124">`wszPathBuffer`zawiera pełną ścieżkę do pliku i jest zerem.</span><span class="sxs-lookup"><span data-stu-id="31db4-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="31db4-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="31db4-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="31db4-126">Bieżący rozmiar `wszPathBuffer` nie jest wystarczająca do przechowywania pełną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="31db4-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="31db4-127">W takim przypadku `pcchPathBuffer` zawiera wymagana liczba `WCHAR`s, w tym znak końcowy null i `GetMetaData` jest wywoływana po raz drugi z rozmiarem buforu żądanej.</span><span class="sxs-lookup"><span data-stu-id="31db4-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31db4-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31db4-128">Remarks</span></span>  
 <span data-ttu-id="31db4-129">Jeśli `wszImagePath` zawiera pełną ścieżkę dla modułu zrzutu Określa ścieżkę z komputera, na którym zrzut został zebrany.</span><span class="sxs-lookup"><span data-stu-id="31db4-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="31db4-130">Plik nie istnieje w tej lokalizacji lub niepoprawny plik o tej samej nazwie może być przechowywany w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="31db4-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31db4-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31db4-131">Requirements</span></span>  
 <span data-ttu-id="31db4-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31db4-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31db4-133">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31db4-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31db4-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31db4-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31db4-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31db4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31db4-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31db4-136">See Also</span></span>  
 [<span data-ttu-id="31db4-137">ICorDebugThread4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="31db4-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="31db4-138">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="31db4-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="31db4-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="31db4-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
