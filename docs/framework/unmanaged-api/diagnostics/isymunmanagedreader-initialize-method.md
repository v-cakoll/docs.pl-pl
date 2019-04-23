---
title: ISymUnmanagedReader::Initialize — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 661c27b9c21f77104b8a86163d3c92d44f8a85df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181782"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="4a414-102">ISymUnmanagedReader::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a414-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="4a414-103">Inicjuje czytnika symboli z interfejsem importera metadanych, które ten czytnik będzie skojarzona, wraz z nazwą pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="4a414-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a414-104">Ta metoda może być wywołana tylko raz i musi zostać wywołana przed wszystkimi metodami czytnika.</span><span class="sxs-lookup"><span data-stu-id="4a414-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a414-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a414-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a414-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a414-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="4a414-107">[in] Interfejs importera metadanych za pomocą którego ten czytnik zostanie skojarzona.</span><span class="sxs-lookup"><span data-stu-id="4a414-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="4a414-108">[in] Nazwa pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="4a414-108">[in] The file name of the module.</span></span> <span data-ttu-id="4a414-109">Możesz użyć `pIStream` parametru zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="4a414-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="4a414-110">[in] Ścieżka do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="4a414-110">[in] The path to search.</span></span> <span data-ttu-id="4a414-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4a414-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="4a414-112">[in] Strumień pliku używana jako alternatywa dla parametru filename.</span><span class="sxs-lookup"><span data-stu-id="4a414-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a414-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4a414-113">Return Value</span></span>  
 <span data-ttu-id="4a414-114">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="4a414-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a414-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a414-115">Remarks</span></span>  
 <span data-ttu-id="4a414-116">Należy określić tylko jeden z `filename` lub `pIStream` parametrów, nie obydwa.</span><span class="sxs-lookup"><span data-stu-id="4a414-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="4a414-117">`searchPath` Parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4a414-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a414-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a414-118">Requirements</span></span>  
 <span data-ttu-id="4a414-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4a414-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a414-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a414-120">See also</span></span>

- [<span data-ttu-id="4a414-121">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a414-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
