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
ms.openlocfilehash: f363bed8e7002bf898755b434c919f8722dea3fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614503"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="100e7-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="100e7-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="100e7-103">Pozwala kompilatorowi pominąć funkcje, które nie zostały zmodyfikowane ze strumienia bazy danych programu (PDB), pod warunkiem, że informacje o wierszu spełniają wymagania.</span><span class="sxs-lookup"><span data-stu-id="100e7-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="100e7-104">Informacje o prawidłowych wierszach można określić ze starymi informacjami o wierszu PDB i jedną różnicą dla wszystkich wierszy w funkcji.</span><span class="sxs-lookup"><span data-stu-id="100e7-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="100e7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="100e7-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="100e7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="100e7-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="100e7-107">podczas Wskaźnik do elementu [IStream](/windows/desktop/api/objidl/nn-objidl-istream) , który zawiera informacje o wierszu.</span><span class="sxs-lookup"><span data-stu-id="100e7-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="100e7-108">podczas Wskaźnik do struktury [SYMLINEDELTA —](symlinedelta-structure.md) , która zawiera wiersze, które uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="100e7-108">[in] A pointer to a [SYMLINEDELTA](symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="100e7-109">podczas `ULONG`Reprezentuje liczbę wierszy, które uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="100e7-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="100e7-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="100e7-110">Return Value</span></span>  
 <span data-ttu-id="100e7-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="100e7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="100e7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="100e7-112">Requirements</span></span>  
 <span data-ttu-id="100e7-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="100e7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="100e7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="100e7-114">See also</span></span>

- [<span data-ttu-id="100e7-115">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="100e7-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
