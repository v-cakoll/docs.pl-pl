---
title: ISymUnmanagedReader::GetSymbolStoreFileName — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b36f4007f286938169cc5d583908493916b9e6f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425343"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="1abca-102">ISymUnmanagedReader::GetSymbolStoreFileName — Metoda</span><span class="sxs-lookup"><span data-stu-id="1abca-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="1abca-103">Zawiera nazwę pliku na dysku magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="1abca-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1abca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1abca-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1abca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1abca-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1abca-106">[in] Rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="1abca-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1abca-107">[out] Wskaźnik do zmiennej, która odbiera długość nazwy zwracane w `szName`, takie jak zakończenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="1abca-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="1abca-108">[out] Wskaźnik do zmiennej, która otrzymuje nazwę pliku w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="1abca-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1abca-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1abca-109">Return Value</span></span>  
 <span data-ttu-id="1abca-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1abca-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1abca-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1abca-111">Requirements</span></span>  
 <span data-ttu-id="1abca-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1abca-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1abca-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1abca-113">See Also</span></span>  
 [<span data-ttu-id="1abca-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="1abca-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
