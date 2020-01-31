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
ms.openlocfilehash: 43f3c1dd866b98bff51b375a11e28727e41d3ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793049"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="5147d-102">ICorDebugMetaDataLocator::GetMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="5147d-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="5147d-103">Prosi debugera o zwrócenie pełnej ścieżki do modułu, którego metadane są wymagane do ukończenia operacji wymaganej przez debuger.</span><span class="sxs-lookup"><span data-stu-id="5147d-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5147d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5147d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="5147d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5147d-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="5147d-106">podczas Ciąg zakończony znakiem null, który reprezentuje pełną ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="5147d-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="5147d-107">Jeśli pełna ścieżka nie jest dostępna, nazwa i rozszerzenie pliku (*filename*. *rozszerzenie*).</span><span class="sxs-lookup"><span data-stu-id="5147d-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="5147d-108">podczas Sygnatura czasowa z nagłówków pliku PE obrazu.</span><span class="sxs-lookup"><span data-stu-id="5147d-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="5147d-109">Ten parametr może być potencjalnie używany dla wyszukiwania serwera symboli ([SymSrv](/windows/desktop/debug/using-symsrv)).</span><span class="sxs-lookup"><span data-stu-id="5147d-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="5147d-110">podczas Rozmiar obrazu z nagłówków pliku PE.</span><span class="sxs-lookup"><span data-stu-id="5147d-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="5147d-111">Ten parametr może być potencjalnie używany dla wyszukiwania SymSrv.</span><span class="sxs-lookup"><span data-stu-id="5147d-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="5147d-112">podczas Liczba znaków w `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5147d-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="5147d-113">określoną Liczba `WCHAR`s zapisywana do `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5147d-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="5147d-114">Jeśli metoda zwraca E_NOT_SUFFICIENT_BUFFER, zawiera liczbę `WCHAR`s wymaganych do przechowania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="5147d-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="5147d-115">określoną Wskaźnik do buforu, do którego debuger skopiuje pełną ścieżkę pliku zawierającego żądane metadane.</span><span class="sxs-lookup"><span data-stu-id="5147d-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="5147d-116">Flaga `ofReadOnly` z wyliczenia [CorOpenFlags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) jest używana do żądania dostępu tylko do odczytu do metadanych w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="5147d-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5147d-117">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="5147d-117">Return Value</span></span>  
 <span data-ttu-id="5147d-118">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="5147d-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="5147d-119">Wszystkie inne błędy HRESULT wskazują, że plik nie jest możliwy do pobierania.</span><span class="sxs-lookup"><span data-stu-id="5147d-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="5147d-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5147d-120">HRESULT</span></span>|<span data-ttu-id="5147d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="5147d-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5147d-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="5147d-122">S_OK</span></span>|<span data-ttu-id="5147d-123">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5147d-123">The method completed successfully.</span></span> <span data-ttu-id="5147d-124">`wszPathBuffer` zawiera pełną ścieżkę do pliku i jest zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="5147d-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="5147d-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5147d-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5147d-126">Bieżący rozmiar `wszPathBuffer` nie jest wystarczający, aby pomieścić pełną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="5147d-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="5147d-127">W tym przypadku `pcchPathBuffer` zawiera wymaganą liczbę `WCHAR`s, w tym kończący znak null, a `GetMetaData` jest wywoływana po raz drugi z żądanym rozmiarem buforu.</span><span class="sxs-lookup"><span data-stu-id="5147d-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5147d-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5147d-128">Remarks</span></span>  
 <span data-ttu-id="5147d-129">Jeśli `wszImagePath` zawiera pełną ścieżkę do modułu ze zrzutu, określa ścieżkę do komputera, na którym został zebrany zrzut.</span><span class="sxs-lookup"><span data-stu-id="5147d-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="5147d-130">Plik może nie istnieć w tej lokalizacji lub w ścieżce może być przechowywany nieprawidłowy plik o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="5147d-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5147d-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5147d-131">Requirements</span></span>  
 <span data-ttu-id="5147d-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5147d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5147d-133">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5147d-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5147d-134">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5147d-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5147d-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5147d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5147d-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5147d-136">See also</span></span>

- [<span data-ttu-id="5147d-137">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="5147d-137">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="5147d-138">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5147d-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5147d-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5147d-139">Debugging</span></span>](index.md)
