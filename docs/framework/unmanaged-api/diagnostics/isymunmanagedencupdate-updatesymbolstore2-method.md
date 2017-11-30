---
title: "ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c0ff6d48bc749b1d8850f94fb1dc1adf3de8e37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="1c76c-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c76c-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="1c76c-103">Umożliwia kompilatora pominąć funkcje, które nie zostały zmodyfikowane ze strumienia programu (PDB) bazy danych, podane informacje dotyczące wiersza spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="1c76c-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="1c76c-104">Starych informacji PDB w wierszu i jeden delta dla wszystkich wierszy w funkcji można określić informacje dotyczące poprawne wiersza.</span><span class="sxs-lookup"><span data-stu-id="1c76c-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c76c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c76c-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c76c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c76c-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="1c76c-107">[in] Wskaźnik do <xref:IStream> zawierający informacje dotyczące wiersza.</span><span class="sxs-lookup"><span data-stu-id="1c76c-107">[in] A pointer to an <xref:IStream> that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="1c76c-108">[in] Wskaźnik do [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) strukturę, która zawiera wiersze, które zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="1c76c-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="1c76c-109">[in] A `ULONG` reprezentujący liczbę wierszy, które zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="1c76c-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c76c-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c76c-110">Return Value</span></span>  
 <span data-ttu-id="1c76c-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1c76c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c76c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c76c-112">Requirements</span></span>  
 <span data-ttu-id="1c76c-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1c76c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c76c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c76c-114">See Also</span></span>  
 [<span data-ttu-id="1c76c-115">ISymUnmanagedENCUpdate — interfejs</span><span class="sxs-lookup"><span data-stu-id="1c76c-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
