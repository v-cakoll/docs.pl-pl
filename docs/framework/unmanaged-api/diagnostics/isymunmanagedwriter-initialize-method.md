---
title: "ISymUnmanagedWriter::Initialize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bae368919941e6a0b234736f789320b62405a17b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="8e16f-102">ISymUnmanagedWriter::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="8e16f-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="8e16f-103">Ustawienie interfejsu nadajnika metadanych, z którą ten moduł zapisujący zostanie skojarzony, a nazwa pliku wyjściowego, na którym zostanie zapisany symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="8e16f-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="8e16f-104">Tę metodę można wywołać tylko raz i musi zostać wywołana przed innych metod składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="8e16f-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="8e16f-105">Niektóre moduły zapisujące może wymagać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="8e16f-105">Some writers may require a file name.</span></span> <span data-ttu-id="8e16f-106">Zawsze można jednak przekazać nazwę pliku do tej metody bez żadnych negatywny wpływ na składniki zapisywania, które nie należy używać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="8e16f-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e16f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e16f-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e16f-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e16f-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="8e16f-109">[in] Wskaźnik do interfejsu nadajnika metadanych.</span><span class="sxs-lookup"><span data-stu-id="8e16f-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="8e16f-110">[in] Nazwa pliku, do którego są zapisywane symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="8e16f-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="8e16f-111">Jeśli nazwa pliku jest określona dla składnika zapisywania, która nie korzysta z nazw plików, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="8e16f-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="8e16f-112">[in] Jeśli zostanie określona, moduł zapisujący symbol będzie Emituj symbole w danym <xref:System.Runtime.InteropServices.ComTypes.IStream> , a nie do pliku określonego w `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="8e16f-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="8e16f-113">`pIStream` Parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8e16f-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="8e16f-114">[in] `true` Jeśli jest to ponownej pełnej kompilacji; `false` Jeśli jest to kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="8e16f-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e16f-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8e16f-115">Return Value</span></span>  
 <span data-ttu-id="8e16f-116">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8e16f-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e16f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e16f-117">Requirements</span></span>  
 <span data-ttu-id="8e16f-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8e16f-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e16f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e16f-119">See Also</span></span>  
 [<span data-ttu-id="8e16f-120">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="8e16f-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="8e16f-121">Initialize2 — metoda</span><span class="sxs-lookup"><span data-stu-id="8e16f-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
