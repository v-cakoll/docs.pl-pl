---
title: "ISymUnmanagedWriter::OpenNamespace — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77d50f6bac87d5a110b53a69044f96f547c51904
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="43048-102">ISymUnmanagedWriter::OpenNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="43048-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="43048-103">Zostanie otwarty nowy obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="43048-103">Opens a new namespace.</span></span> <span data-ttu-id="43048-104">Tę metodę należy wywołać przed zdefiniowaniem metod lub zmienne, które zajmują przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="43048-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="43048-105">Przestrzenie nazw mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="43048-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43048-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="43048-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43048-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="43048-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="43048-108">[in] Wskaźnik na nazwę nowej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="43048-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43048-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="43048-109">Return Value</span></span>  
 <span data-ttu-id="43048-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="43048-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43048-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43048-111">Requirements</span></span>  
 <span data-ttu-id="43048-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="43048-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43048-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43048-113">See Also</span></span>  
 [<span data-ttu-id="43048-114">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="43048-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="43048-115">CloseNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="43048-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
