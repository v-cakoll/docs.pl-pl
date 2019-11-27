---
title: ISymUnmanagedWriter::Initialize — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
ms.openlocfilehash: 6e9ab623d5fe9fcfda2305df078e988a561afdc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427977"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="de626-102">ISymUnmanagedWriter::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="de626-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="de626-103">Ustawia interfejs emitujący metadane, z którym jest skojarzony ten składnik zapisywania i ustawia nazwę pliku wyjściowego, do którego będą zapisywane symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="de626-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="de626-104">Tę metodę można wywołać tylko raz i musi ona zostać wywołana przed innymi metodami zapisywania.</span><span class="sxs-lookup"><span data-stu-id="de626-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="de626-105">Niektóre moduły zapisujące mogą wymagać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="de626-105">Some writers may require a file name.</span></span> <span data-ttu-id="de626-106">Można jednak zawsze przekazać nazwę pliku do tej metody bez żadnego negatywnego wpływu na moduły zapisujące, które nie używają nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="de626-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de626-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="de626-107">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de626-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="de626-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="de626-109">podczas Wskaźnik do interfejsu emitującego metadane.</span><span class="sxs-lookup"><span data-stu-id="de626-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="de626-110">podczas Nazwa pliku, do którego są zapisywane symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="de626-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="de626-111">Jeśli nazwa pliku jest określona dla składnika zapisywania, który nie używa nazw plików, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="de626-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="de626-112">podczas Jeśli ta wartość jest określona, moduł zapisujący symboli będzie emituje symbole do danego <xref:System.Runtime.InteropServices.ComTypes.IStream>, a nie do pliku określonego w parametrze `filename`.</span><span class="sxs-lookup"><span data-stu-id="de626-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="de626-113">Parametr `pIStream` jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="de626-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="de626-114">[in] `true`, jeśli jest to pełna kompilacja; `false`, jeśli jest to kompilacja przyrostowa.</span><span class="sxs-lookup"><span data-stu-id="de626-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de626-115">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="de626-115">Return Value</span></span>  
 <span data-ttu-id="de626-116">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="de626-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de626-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de626-117">Requirements</span></span>  
 <span data-ttu-id="de626-118">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="de626-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de626-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de626-119">See also</span></span>

- [<span data-ttu-id="de626-120">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="de626-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="de626-121">Initialize2, metoda</span><span class="sxs-lookup"><span data-stu-id="de626-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
