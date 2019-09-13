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
ms.openlocfilehash: 11dc050e2fe16a64db4ac95bb1386e2d90535e81
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895027"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="657a9-102">ISymUnmanagedWriter::SetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="657a9-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="657a9-103">Określa metodę zdefiniowaną przez użytkownika, która jest punktem wejścia dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="657a9-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="657a9-104">Na przykład ten punkt wejścia może być główną metodą użytkownika zamiast wygenerowanymi przez kompilator wycinków przed głównym.</span><span class="sxs-lookup"><span data-stu-id="657a9-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="657a9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="657a9-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="657a9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="657a9-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="657a9-107">podczas Token metadanych dla metody, która jest punktem wejścia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="657a9-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="657a9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="657a9-108">Return Value</span></span>  
 <span data-ttu-id="657a9-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie, E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="657a9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="657a9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="657a9-110">Requirements</span></span>  
 <span data-ttu-id="657a9-111">**Nagłówki** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="657a9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657a9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="657a9-112">See also</span></span>

- [<span data-ttu-id="657a9-113">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="657a9-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
