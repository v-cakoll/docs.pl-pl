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
ms.openlocfilehash: 417cf623948d16147f9a1242d714f4df1311a314
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700946"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="474e7-102">ISymUnmanagedWriter::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="474e7-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="474e7-103">Ustawia interfejsu nadajnika metadanych, z którym ten moduł zapisujący zostanie skojarzona i ustawia nazwę pliku wyjściowego, do którego symbole debugowania zostaną zapisane.</span><span class="sxs-lookup"><span data-stu-id="474e7-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="474e7-104">Ta metoda może być wywoływana tylko raz, a musi zostać wywołana przed innymi metodami składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="474e7-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="474e7-105">Niektóre moduły zapisujące może wymagać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="474e7-105">Some writers may require a file name.</span></span> <span data-ttu-id="474e7-106">Zawsze można jednak przekazać nazwę pliku do tej metody bez żadnych negatywny wpływ na modułów zapisujących, które nie korzystają z nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="474e7-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="474e7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="474e7-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="474e7-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="474e7-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="474e7-109">[in] Wskaźnik do interfejsu nadajnika metadanych.</span><span class="sxs-lookup"><span data-stu-id="474e7-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="474e7-110">[in] Nazwa pliku, do którego symbole debugowania są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="474e7-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="474e7-111">Jeśli nazwa pliku jest określony dla modułu zapisującego, która nie korzysta z nazw plików, ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="474e7-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="474e7-112">[in] Jeśli zostanie określony, moduł zapisujący symbol zostanie wyemitowany symbole w danym <xref:System.Runtime.InteropServices.ComTypes.IStream> , a nie do pliku określonego w `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="474e7-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="474e7-113">`pIStream` Parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="474e7-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="474e7-114">[in] `true` Jeśli po ponownej pełnej kompilacji; `false` Jeśli jest to kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="474e7-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="474e7-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="474e7-115">Return Value</span></span>  
 <span data-ttu-id="474e7-116">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="474e7-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="474e7-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="474e7-117">Requirements</span></span>  
 <span data-ttu-id="474e7-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="474e7-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="474e7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="474e7-119">See also</span></span>

- [<span data-ttu-id="474e7-120">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="474e7-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="474e7-121">Initialize2, metoda</span><span class="sxs-lookup"><span data-stu-id="474e7-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
