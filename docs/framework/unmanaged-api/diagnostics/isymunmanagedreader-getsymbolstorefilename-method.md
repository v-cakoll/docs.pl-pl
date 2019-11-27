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
ms.openlocfilehash: b3674c4058dba2f6185418b55b35eefb14c312f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431239"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="d1b07-102">ISymUnmanagedReader::GetSymbolStoreFileName — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1b07-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="d1b07-103">Udostępnia nazwę pliku na dysku magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="d1b07-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1b07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1b07-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1b07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1b07-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d1b07-106">podczas Rozmiar buforu `szName`.</span><span class="sxs-lookup"><span data-stu-id="d1b07-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d1b07-107">określoną Wskaźnik do zmiennej, która otrzymuje długość nazwy zwróconej w `szName`, łącznie z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="d1b07-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="d1b07-108">określoną Wskaźnik do zmiennej, która otrzymuje nazwę pliku magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="d1b07-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1b07-109">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="d1b07-109">Return Value</span></span>  
 <span data-ttu-id="d1b07-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d1b07-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1b07-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1b07-111">Requirements</span></span>  
 <span data-ttu-id="d1b07-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d1b07-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b07-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1b07-113">See also</span></span>

- [<span data-ttu-id="d1b07-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1b07-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
