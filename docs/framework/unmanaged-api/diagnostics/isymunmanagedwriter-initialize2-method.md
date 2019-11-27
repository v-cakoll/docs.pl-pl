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
ms.openlocfilehash: 041df959139a0be77f40d6aa5655ff15f93fb26f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427941"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="2f53b-102">ISymUnmanagedWriter::Initialize2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="2f53b-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="2f53b-103">Ustawia interfejs emitujący metadane, z którym jest skojarzony ten składnik zapisywania i ustawia nazwę pliku wyjściowego, do którego będą zapisywane symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="2f53b-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="2f53b-104">Ta metoda umożliwia również ustawienie końcowej lokalizacji pliku bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="2f53b-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f53b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f53b-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f53b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f53b-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="2f53b-107">podczas Wskaźnik do interfejsu emitującego metadane.</span><span class="sxs-lookup"><span data-stu-id="2f53b-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="2f53b-108">podczas Wskaźnik do `WCHAR`, który zawiera nazwę pliku, do którego są zapisywane symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="2f53b-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="2f53b-109">Jeśli nazwa pliku jest określona dla składnika zapisywania, który nie używa nazw plików, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="2f53b-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="2f53b-110">podczas Jeśli ta wartość jest określona, moduł zapisujący symboli emituje symbole do danego <xref:System.Runtime.InteropServices.ComTypes.IStream>, a nie do pliku określonego w parametrze `filename`.</span><span class="sxs-lookup"><span data-stu-id="2f53b-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="2f53b-111">Parametr `pIStream` jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2f53b-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="2f53b-112">[in] `true`, jeśli jest to pełna kompilacja; `false`, jeśli jest to kompilacja przyrostowa.</span><span class="sxs-lookup"><span data-stu-id="2f53b-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="2f53b-113">podczas Wskaźnik do `WCHAR`, który jest ciągiem ścieżki do ostatecznej lokalizacji pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="2f53b-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f53b-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2f53b-114">Return Value</span></span>  
 <span data-ttu-id="2f53b-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2f53b-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f53b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f53b-116">Requirements</span></span>  
 <span data-ttu-id="2f53b-117">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2f53b-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f53b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f53b-118">See also</span></span>

- [<span data-ttu-id="2f53b-119">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f53b-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="2f53b-120">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="2f53b-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
