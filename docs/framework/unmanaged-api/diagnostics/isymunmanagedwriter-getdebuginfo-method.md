---
title: ISymUnmanagedWriter::GetDebugInfo — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce74b043db67fa1086724dd76001935f9c1c0498
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470955"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="468f2-102">ISymUnmanagedWriter::GetDebugInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="468f2-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="468f2-103">Zwraca informacje niezbędne do kompilatora zapisać wpis katalogu debugowania w przenośnych nagłówka pliku wykonywalnego (PE).</span><span class="sxs-lookup"><span data-stu-id="468f2-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="468f2-104">Moduł zapisujący symbol wypełni wszystkie pola z wyjątkiem `TimeDateStamp` i `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="468f2-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="468f2-105">(Kompilator jest odpowiedzialny za odpowiednie ustawienie tych dwóch pól).</span><span class="sxs-lookup"><span data-stu-id="468f2-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="468f2-106">Kompilatora powinna wywołać tę metodę, emisji obiektu blob danych do pliku PE, ustawianie `PointerToRawData` pole IMAGE_DEBUG_DIRECTORY polecenie emitowany dane i zapisać IMAGE_DEBUG_DIRECTORY do pliku PE.</span><span class="sxs-lookup"><span data-stu-id="468f2-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="468f2-107">Kompilator należy również ustawić `TimeDateStamp` równą `TimeDateStamp` pliku PE generowane.</span><span class="sxs-lookup"><span data-stu-id="468f2-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="468f2-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="468f2-108">Syntax</span></span>  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="468f2-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="468f2-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="468f2-110">[out w] Wskaźnik do IMAGE_DEBUG_DIRECTORY, który wypełni moduł zapisujący symboli.</span><span class="sxs-lookup"><span data-stu-id="468f2-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="468f2-111">[in] Element `DWORD` zawierający rozmiar danych debugowania.</span><span class="sxs-lookup"><span data-stu-id="468f2-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="468f2-112">[out] Wskaźnik do `DWORD` odbierająca rozmiar buforu, muszą zawierać dane debugowania.</span><span class="sxs-lookup"><span data-stu-id="468f2-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="468f2-113">[out] Wskaźnik do buforu, który jest wystarczająco duży, aby pomieścić dane debugowania do magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="468f2-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="468f2-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="468f2-114">Return Value</span></span>  
 <span data-ttu-id="468f2-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="468f2-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="468f2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="468f2-116">Requirements</span></span>  
 <span data-ttu-id="468f2-117">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="468f2-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="468f2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="468f2-118">See also</span></span>
- [<span data-ttu-id="468f2-119">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="468f2-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
