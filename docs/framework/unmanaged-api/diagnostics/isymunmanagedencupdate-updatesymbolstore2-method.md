---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82f2f335299cfd3041dcecc7d176cb77ce54ae96
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172136"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="b19b5-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="b19b5-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="b19b5-103">Umożliwia kompilatorowi pominąć funkcje, które nie zostały zmodyfikowane ze strumienia bazy danych (PDB) programu, pod warunkiem informacje wiersza spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="b19b5-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="b19b5-104">Informacje wiersza poprawne można ustalić przy użyciu starych informacji PDB w wierszu i jeden różnicowej dla wszystkich wierszy w funkcji.</span><span class="sxs-lookup"><span data-stu-id="b19b5-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19b5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b19b5-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b19b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b19b5-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="b19b5-107">[in] Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) zawierający informacje wiersza.</span><span class="sxs-lookup"><span data-stu-id="b19b5-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="b19b5-108">[in] Wskaźnik do [symlinedelta —](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) strukturę, która zawiera wiersze, które uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="b19b5-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="b19b5-109">[in] A `ULONG` reprezentujący liczbę wierszy, które uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="b19b5-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b19b5-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b19b5-110">Return Value</span></span>  
 <span data-ttu-id="b19b5-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="b19b5-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b19b5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b19b5-112">Requirements</span></span>  
 <span data-ttu-id="b19b5-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b19b5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19b5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b19b5-114">See also</span></span>

- [<span data-ttu-id="b19b5-115">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="b19b5-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
