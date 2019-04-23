---
title: ISymUnmanagedWriter::SetUserEntryPoint — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d14d542a8c1d8adeaf56dc1564e8e10121cd4064
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224224"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="d0bb6-102">ISymUnmanagedWriter::SetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0bb6-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="d0bb6-103">Określa metodę zdefiniowanych przez użytkownika, który jest punktem wejścia dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="d0bb6-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="d0bb6-104">Na przykład ten punkt wejścia, może być metoda głównego użytkownika zamiast wycinków generowanych przez kompilator przed funkcją main.</span><span class="sxs-lookup"><span data-stu-id="d0bb6-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0bb6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0bb6-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0bb6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0bb6-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="d0bb6-107">[in] Token metadanych dla metody, która jest wpis użytkownika punktu.</span><span class="sxs-lookup"><span data-stu-id="d0bb6-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0bb6-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0bb6-108">Return Value</span></span>  
 <span data-ttu-id="d0bb6-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="d0bb6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0bb6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0bb6-110">Requirements</span></span>  
 <span data-ttu-id="d0bb6-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d0bb6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0bb6-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0bb6-112">See also</span></span>

- [<span data-ttu-id="d0bb6-113">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0bb6-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
