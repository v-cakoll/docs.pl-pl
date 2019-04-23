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
ms.openlocfilehash: 147b33a3f49f9163daea776779ca26f62561a84e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170381"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="9cbe1-102">ISymUnmanagedReader::GetSymbolStoreFileName — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cbe1-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="9cbe1-103">Zawiera nazwę pliku na dysku w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="9cbe1-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cbe1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cbe1-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cbe1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cbe1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9cbe1-106">[in] Rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="9cbe1-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9cbe1-107">[out] Wskaźnik do zmiennej, która odbiera długość nazwy zwracane w `szName`, łącznie z zakończenia o wartości null.</span><span class="sxs-lookup"><span data-stu-id="9cbe1-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="9cbe1-108">[out] Wskaźnik do zmiennej, która otrzymuje nazwę pliku w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="9cbe1-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cbe1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9cbe1-109">Return Value</span></span>  
 <span data-ttu-id="9cbe1-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="9cbe1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cbe1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cbe1-111">Requirements</span></span>  
 <span data-ttu-id="9cbe1-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9cbe1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbe1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cbe1-113">See also</span></span>

- [<span data-ttu-id="9cbe1-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cbe1-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
