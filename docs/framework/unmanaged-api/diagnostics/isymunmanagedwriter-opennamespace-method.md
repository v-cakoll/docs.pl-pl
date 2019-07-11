---
title: ISymUnmanagedWriter::OpenNamespace — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bd07411acd074bf5a25148110dbdf28a004551a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777246"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="a5891-102">ISymUnmanagedWriter::OpenNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="a5891-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="a5891-103">Zostanie otwarty nowy obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="a5891-103">Opens a new namespace.</span></span> <span data-ttu-id="a5891-104">Tę metodę należy wywołać przed zdefiniowaniem metody lub zmienne, które zajmują przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a5891-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="a5891-105">Przestrzenie nazw mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="a5891-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5891-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5891-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5891-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5891-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a5891-108">[in] Wskaźnik na nazwę nowej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a5891-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5891-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a5891-109">Return Value</span></span>  
 <span data-ttu-id="a5891-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="a5891-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5891-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5891-111">Requirements</span></span>  
 <span data-ttu-id="a5891-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a5891-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5891-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5891-113">See also</span></span>

- [<span data-ttu-id="a5891-114">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5891-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a5891-115">CloseNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="a5891-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
