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
ms.openlocfilehash: 5917fbe3cebe9b1e9ab91d113aee2461f414c14d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="c1ad7-102">ISymUnmanagedReader::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1ad7-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="c1ad7-103">Inicjuje czytnika symboli z interfejsem importer metadanych, który tego czytnika zostanie skojarzona z, wraz z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1ad7-104">Ta metoda może być wywołana tylko raz i musi zostać wywołana przed innymi metodami czytnika.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ad7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1ad7-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1ad7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1ad7-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="c1ad7-107">[in] Interfejs importer metadanych, z którą zostanie skojarzona tego czytnika.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="c1ad7-108">[in] Nazwa pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-108">[in] The file name of the module.</span></span> <span data-ttu-id="c1ad7-109">Można użyć `pIStream` parametru zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="c1ad7-110">[in] Ścieżka do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-110">[in] The path to search.</span></span> <span data-ttu-id="c1ad7-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="c1ad7-112">[in] Strumień pliku używany jako alternatywę dla parametru filename.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1ad7-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c1ad7-113">Return Value</span></span>  
 <span data-ttu-id="c1ad7-114">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1ad7-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1ad7-115">Remarks</span></span>  
 <span data-ttu-id="c1ad7-116">Należy określić tylko jeden z `filename` lub `pIStream` parametrów nie oba.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="c1ad7-117">`searchPath` Parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ad7-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1ad7-118">Requirements</span></span>  
 <span data-ttu-id="c1ad7-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c1ad7-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ad7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1ad7-120">See Also</span></span>  
 [<span data-ttu-id="c1ad7-121">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="c1ad7-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
