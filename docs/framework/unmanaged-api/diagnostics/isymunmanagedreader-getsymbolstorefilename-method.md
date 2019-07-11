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
ms.openlocfilehash: 50cd6d1e3666dd1f15c1e6a6b4f7dcb931b79d8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777062"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="0c22d-102">ISymUnmanagedReader::GetSymbolStoreFileName — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c22d-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="0c22d-103">Zawiera nazwę pliku na dysku w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="0c22d-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c22d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c22d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c22d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c22d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0c22d-106">[in] Rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="0c22d-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0c22d-107">[out] Wskaźnik do zmiennej, która odbiera długość nazwy zwracane w `szName`, łącznie z zakończenia o wartości null.</span><span class="sxs-lookup"><span data-stu-id="0c22d-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="0c22d-108">[out] Wskaźnik do zmiennej, która otrzymuje nazwę pliku w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="0c22d-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c22d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0c22d-109">Return Value</span></span>  
 <span data-ttu-id="0c22d-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="0c22d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c22d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c22d-111">Requirements</span></span>  
 <span data-ttu-id="0c22d-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0c22d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c22d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c22d-113">See also</span></span>

- [<span data-ttu-id="0c22d-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c22d-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
