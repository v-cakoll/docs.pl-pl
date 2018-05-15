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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44046560f4f788c4a7d695ff18c9c01740fea35a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="04f22-102">ISymUnmanagedWriter::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="04f22-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="04f22-103">Ustawienie interfejsu nadajnika metadanych, z którą ten moduł zapisujący zostanie skojarzony, a nazwa pliku wyjściowego, na którym zostanie zapisany symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="04f22-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="04f22-104">Tę metodę można wywołać tylko raz i musi zostać wywołana przed innych metod składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="04f22-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="04f22-105">Niektóre moduły zapisujące może wymagać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="04f22-105">Some writers may require a file name.</span></span> <span data-ttu-id="04f22-106">Zawsze można jednak przekazać nazwę pliku do tej metody bez żadnych negatywny wpływ na składniki zapisywania, które nie należy używać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="04f22-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f22-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="04f22-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04f22-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="04f22-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="04f22-109">[in] Wskaźnik do interfejsu nadajnika metadanych.</span><span class="sxs-lookup"><span data-stu-id="04f22-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="04f22-110">[in] Nazwa pliku, do którego są zapisywane symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="04f22-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="04f22-111">Jeśli nazwa pliku jest określona dla składnika zapisywania, która nie korzysta z nazw plików, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="04f22-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="04f22-112">[in] Jeśli zostanie określona, moduł zapisujący symbol będzie Emituj symbole w danym <xref:System.Runtime.InteropServices.ComTypes.IStream> , a nie do pliku określonego w `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="04f22-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="04f22-113">`pIStream` Parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="04f22-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="04f22-114">[in] `true` Jeśli jest to ponownej pełnej kompilacji; `false` Jeśli jest to kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="04f22-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04f22-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="04f22-115">Return Value</span></span>  
 <span data-ttu-id="04f22-116">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="04f22-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04f22-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04f22-117">Requirements</span></span>  
 <span data-ttu-id="04f22-118">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="04f22-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f22-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04f22-119">See Also</span></span>  
 [<span data-ttu-id="04f22-120">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="04f22-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="04f22-121">Initialize2, metoda</span><span class="sxs-lookup"><span data-stu-id="04f22-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
