---
title: ICorDebugMetaDataLocator::GetMetaData — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c29e581a77ac90882d102cfee2c715e9c309e1a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116028"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="89e19-102">ICorDebugMetaDataLocator::GetMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="89e19-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="89e19-103">Pyta, czy debugera, aby przywrócić pełną ścieżkę do modułu, którego metadanych jest potrzebne do ukończenia operacja, którą żądany debuger.</span><span class="sxs-lookup"><span data-stu-id="89e19-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89e19-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="89e19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89e19-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="89e19-106">[in] Ciąg zakończony znakiem null, który reprezentuje pełną ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="89e19-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="89e19-107">Jeśli pełna ścieżka nie jest dostępna, nazwę i rozszerzenie nazwy pliku (*filename*. *rozszerzenie*).</span><span class="sxs-lookup"><span data-stu-id="89e19-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="89e19-108">[in] Sygnatura czasowa z nagłówków pliku PE obrazu.</span><span class="sxs-lookup"><span data-stu-id="89e19-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="89e19-109">Ten parametr potencjalnie może służyć do serwera symboli ([SymSrv](/windows/desktop/debug/using-symsrv)) wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="89e19-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="89e19-110">[in] Rozmiar obrazu z nagłówków pliku PE.</span><span class="sxs-lookup"><span data-stu-id="89e19-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="89e19-111">Ten parametr potencjalnie może służyć do wyszukiwania SymSrv.</span><span class="sxs-lookup"><span data-stu-id="89e19-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="89e19-112">[in] Znak liczby w `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="89e19-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="89e19-113">[out] Liczba `WCHAR`s zapisywane `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="89e19-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="89e19-114">Jeśli metoda zwraca E_NOT_SUFFICIENT_BUFFER, zawiera liczbę `WCHAR`s niezbędne do przechowywania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="89e19-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="89e19-115">[out] Wskaźnik do buforu, do którego debuger będzie skopiować pełną ścieżkę pliku, który zawiera żądane metadanych.</span><span class="sxs-lookup"><span data-stu-id="89e19-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="89e19-116">`ofReadOnly` Flaga z [coropenflags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczenie jest używane, aby zażądać dostępu tylko do odczytu do metadanych, w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="89e19-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89e19-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="89e19-117">Return Value</span></span>  
 <span data-ttu-id="89e19-118">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="89e19-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="89e19-119">Wszystkie inne wartości HRESULT błędu wskazują, że plik nie jest możliwe do pobierania.</span><span class="sxs-lookup"><span data-stu-id="89e19-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="89e19-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89e19-120">HRESULT</span></span>|<span data-ttu-id="89e19-121">Opis</span><span class="sxs-lookup"><span data-stu-id="89e19-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89e19-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="89e19-122">S_OK</span></span>|<span data-ttu-id="89e19-123">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="89e19-123">The method completed successfully.</span></span> <span data-ttu-id="89e19-124">`wszPathBuffer` zawiera pełną ścieżkę do pliku i jest zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="89e19-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="89e19-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="89e19-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="89e19-126">Bieżący rozmiar `wszPathBuffer` nie jest wystarczająca do przechowywania pełnej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="89e19-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="89e19-127">W tym przypadku `pcchPathBuffer` zawiera wymagana liczba `WCHAR`s, łącznie z końcowym znakiem zerowym, i `GetMetaData` jest wywoływana po raz drugi z rozmiarem buforu żądanej.</span><span class="sxs-lookup"><span data-stu-id="89e19-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89e19-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89e19-128">Remarks</span></span>  
 <span data-ttu-id="89e19-129">Jeśli `wszImagePath` zawiera pełną ścieżkę dla modułu zrzutu, określa ścieżkę z komputera, w której pobrano zrzut.</span><span class="sxs-lookup"><span data-stu-id="89e19-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="89e19-130">Plik nie istnieje w tej lokalizacji lub niepoprawny plik o takiej samej nazwie, mogą być przechowywane w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="89e19-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e19-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89e19-131">Requirements</span></span>  
 <span data-ttu-id="89e19-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89e19-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e19-133">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89e19-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89e19-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89e19-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89e19-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e19-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e19-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89e19-136">See also</span></span>

- [<span data-ttu-id="89e19-137">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="89e19-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="89e19-138">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="89e19-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="89e19-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="89e19-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
