---
title: ISymUnmanagedWriter::Initialize2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71eeeefc594c450d5fb95ebae17e3c1316301278
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481381"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="50562-102">ISymUnmanagedWriter::Initialize2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="50562-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="50562-103">Ustawia interfejsu nadajnika metadanych, z którym ten moduł zapisujący zostanie skojarzona i ustawia nazwę pliku wyjściowego, do którego symbole debugowania zostaną zapisane.</span><span class="sxs-lookup"><span data-stu-id="50562-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="50562-104">Ta metoda umożliwia również ustawić ostateczny lokalizacja pliku bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="50562-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50562-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="50562-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50562-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="50562-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="50562-107">[in] Wskaźnik do interfejsu nadajnika metadanych.</span><span class="sxs-lookup"><span data-stu-id="50562-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="50562-108">[in] Wskaźnik do `WCHAR` zawierający nazwę pliku, do którego symbole debugowania są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="50562-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="50562-109">Jeśli nazwa pliku jest określony dla modułu zapisującego, która nie korzysta z nazw plików, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="50562-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="50562-110">[in] Jeśli zostanie określony, moduł zapisujący symbol emituje symbole w danym <xref:System.Runtime.InteropServices.ComTypes.IStream> , a nie do pliku określonego w `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="50562-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="50562-111">`pIStream` Parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="50562-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="50562-112">[in] `true` Jeśli po ponownej pełnej kompilacji; `false` Jeśli jest to kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="50562-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="50562-113">[in] Wskaźnik do `WCHAR` czyli ciąg ścieżki do ostatecznego lokalizacji pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="50562-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50562-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50562-114">Return Value</span></span>  
 <span data-ttu-id="50562-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="50562-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50562-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50562-116">Requirements</span></span>  
 <span data-ttu-id="50562-117">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="50562-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50562-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50562-118">See also</span></span>
- [<span data-ttu-id="50562-119">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="50562-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="50562-120">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="50562-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
