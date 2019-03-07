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
ms.openlocfilehash: 3bd3d411ad6fe7f65d1eeb25754794704752009e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488360"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="53aa7-102">ISymUnmanagedWriter::SetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="53aa7-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="53aa7-103">Określa metodę zdefiniowanych przez użytkownika, który jest punktem wejścia dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="53aa7-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="53aa7-104">Na przykład ten punkt wejścia, może być metoda głównego użytkownika zamiast wycinków generowanych przez kompilator przed funkcją main.</span><span class="sxs-lookup"><span data-stu-id="53aa7-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53aa7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="53aa7-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53aa7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="53aa7-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="53aa7-107">[in] Token metadanych dla metody, która jest wpis użytkownika punktu.</span><span class="sxs-lookup"><span data-stu-id="53aa7-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53aa7-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="53aa7-108">Return Value</span></span>  
 <span data-ttu-id="53aa7-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="53aa7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53aa7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53aa7-110">Requirements</span></span>  
 <span data-ttu-id="53aa7-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="53aa7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53aa7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53aa7-112">See also</span></span>
- [<span data-ttu-id="53aa7-113">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="53aa7-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
