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
ms.openlocfilehash: acbd49de7362d9c05a609a2d870af100637e10ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427904"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="73a28-102">ISymUnmanagedWriter::OpenNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="73a28-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="73a28-103">Otwiera nową przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="73a28-103">Opens a new namespace.</span></span> <span data-ttu-id="73a28-104">Wywołaj tę metodę przed zdefiniowaniem metod lub zmiennych, które zajmują przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="73a28-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="73a28-105">Przestrzenie nazw mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="73a28-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a28-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="73a28-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73a28-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="73a28-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="73a28-108">podczas Wskaźnik do nazwy nowej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="73a28-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73a28-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73a28-109">Return Value</span></span>  
 <span data-ttu-id="73a28-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="73a28-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73a28-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73a28-111">Requirements</span></span>  
 <span data-ttu-id="73a28-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="73a28-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a28-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73a28-113">See also</span></span>

- [<span data-ttu-id="73a28-114">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="73a28-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="73a28-115">CloseNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="73a28-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
