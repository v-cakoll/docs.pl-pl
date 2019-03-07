---
title: ISymUnmanagedWriter::UsingNamespace — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b102f49a642d2bcd62e7f75a8dd0b9ab782ad674
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491350"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="46826-102">ISymUnmanagedWriter::UsingNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="46826-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="46826-103">Określa, że dany w pełni kwalifikowanej nazwy obszaru nazw jest używany w zakresie leksykalnym aktualnie otwarte.</span><span class="sxs-lookup"><span data-stu-id="46826-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="46826-104">Przestrzeń nazw będzie używany w ramach wszystkie zakresy, które dziedziczą z aktualnie otwartego zakresu.</span><span class="sxs-lookup"><span data-stu-id="46826-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="46826-105">Zamyka bieżący zakres spowoduje również przerwanie użycie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46826-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46826-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="46826-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46826-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="46826-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="46826-108">[in] Wskaźnik do w pełni kwalifikowaną nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46826-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46826-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="46826-109">Return Value</span></span>  
 <span data-ttu-id="46826-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="46826-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46826-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46826-111">Requirements</span></span>  
 <span data-ttu-id="46826-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="46826-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46826-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46826-113">See also</span></span>
- [<span data-ttu-id="46826-114">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="46826-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
