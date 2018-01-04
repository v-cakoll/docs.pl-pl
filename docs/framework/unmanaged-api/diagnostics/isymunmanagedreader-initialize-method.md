---
title: "ISymUnmanagedReader::Initialize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 433cd62f7801d386f3b34b7fc8e95bd1d0c5f765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="e53d8-102">ISymUnmanagedReader::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="e53d8-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="e53d8-103">Inicjuje czytnika symboli z interfejsem importer metadanych, który tego czytnika zostanie skojarzona z, wraz z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="e53d8-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e53d8-104">Ta metoda może być wywołana tylko raz i musi zostać wywołana przed innymi metodami czytnika.</span><span class="sxs-lookup"><span data-stu-id="e53d8-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53d8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e53d8-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e53d8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e53d8-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="e53d8-107">[in] Interfejs importer metadanych, z którą zostanie skojarzona tego czytnika.</span><span class="sxs-lookup"><span data-stu-id="e53d8-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="e53d8-108">[in] Nazwa pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="e53d8-108">[in] The file name of the module.</span></span> <span data-ttu-id="e53d8-109">Można użyć `pIStream` parametru zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e53d8-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="e53d8-110">[in] Ścieżka do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e53d8-110">[in] The path to search.</span></span> <span data-ttu-id="e53d8-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e53d8-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="e53d8-112">[in] Strumień pliku używany jako alternatywę dla parametru filename.</span><span class="sxs-lookup"><span data-stu-id="e53d8-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e53d8-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e53d8-113">Return Value</span></span>  
 <span data-ttu-id="e53d8-114">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e53d8-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e53d8-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e53d8-115">Remarks</span></span>  
 <span data-ttu-id="e53d8-116">Należy określić tylko jeden z `filename` lub `pIStream` parametrów nie oba.</span><span class="sxs-lookup"><span data-stu-id="e53d8-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="e53d8-117">`searchPath` Parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e53d8-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e53d8-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e53d8-118">Requirements</span></span>  
 <span data-ttu-id="e53d8-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e53d8-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53d8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e53d8-120">See Also</span></span>  
 [<span data-ttu-id="e53d8-121">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="e53d8-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
