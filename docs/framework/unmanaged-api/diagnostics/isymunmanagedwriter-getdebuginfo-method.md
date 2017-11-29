---
title: "ISymUnmanagedWriter::GetDebugInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 562e9015f2aa402a90a7b31e4b7002e68893a812
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="b395e-102">ISymUnmanagedWriter::GetDebugInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="b395e-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="b395e-103">Zwraca informacje niezbędne do kompilatora, aby zapisać wpis katalogu debugowania w przenośnych nagłówka pliku wykonywalnego (PE).</span><span class="sxs-lookup"><span data-stu-id="b395e-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="b395e-104">Moduł zapisujący symbol wypełnia wszystkie pola z wyjątkiem `TimeDateStamp` i `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="b395e-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="b395e-105">(Kompilator jest odpowiedzialny za odpowiednie ustawienie tych dwóch pól).</span><span class="sxs-lookup"><span data-stu-id="b395e-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="b395e-106">Kompilator powinien wywołać tę metodę, Emituj danych obiektu blob do pliku PE, ustaw `PointerToRawData` w IMAGE_DEBUG_DIRECTORY polecenie emitowany dane i zapis IMAGE_DEBUG_DIRECTORY pliku PE.</span><span class="sxs-lookup"><span data-stu-id="b395e-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="b395e-107">Kompilator należy również ustawić `TimeDateStamp` równą `TimeDateStamp` Trwa generowanie pliku PE.</span><span class="sxs-lookup"><span data-stu-id="b395e-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b395e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b395e-108">Syntax</span></span>  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b395e-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="b395e-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="b395e-110">[w, out] Wskaźnik do IMAGE_DEBUG_DIRECTORY, który wypełnia twórcę symbolu.</span><span class="sxs-lookup"><span data-stu-id="b395e-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="b395e-111">[in] A `DWORD` zawierający rozmiar danych debugowania.</span><span class="sxs-lookup"><span data-stu-id="b395e-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="b395e-112">[out] Wskaźnik do `DWORD` odbierająca rozmiar buforu, muszą zawierać dane debugowania.</span><span class="sxs-lookup"><span data-stu-id="b395e-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="b395e-113">[out] Wskaźnik do buforu, który jest wystarczająco duży, aby pomieścić dane magazynu symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="b395e-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b395e-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b395e-114">Return Value</span></span>  
 <span data-ttu-id="b395e-115">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b395e-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b395e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b395e-116">Requirements</span></span>  
 <span data-ttu-id="b395e-117">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b395e-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b395e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b395e-118">See Also</span></span>  
 [<span data-ttu-id="b395e-119">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="b395e-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
