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
ms.openlocfilehash: 5a4bcc4e6994f06fabf69e5548ad6922343b7dd5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479795"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="371ce-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="371ce-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="371ce-103">Umożliwia kompilatorowi pominąć funkcje, które nie zostały zmodyfikowane ze strumienia bazy danych (PDB) programu, pod warunkiem informacje wiersza spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="371ce-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="371ce-104">Informacje wiersza poprawne można ustalić przy użyciu starych informacji PDB w wierszu i jeden różnicowej dla wszystkich wierszy w funkcji.</span><span class="sxs-lookup"><span data-stu-id="371ce-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="371ce-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="371ce-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="371ce-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="371ce-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="371ce-107">[in] Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) zawierający informacje wiersza.</span><span class="sxs-lookup"><span data-stu-id="371ce-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="371ce-108">[in] Wskaźnik do [symlinedelta —](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) strukturę, która zawiera wiersze, które uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="371ce-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="371ce-109">[in] A `ULONG` reprezentujący liczbę wierszy, które uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="371ce-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="371ce-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="371ce-110">Return Value</span></span>  
 <span data-ttu-id="371ce-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="371ce-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="371ce-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="371ce-112">Requirements</span></span>  
 <span data-ttu-id="371ce-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="371ce-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="371ce-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="371ce-114">See also</span></span>
- [<span data-ttu-id="371ce-115">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="371ce-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
