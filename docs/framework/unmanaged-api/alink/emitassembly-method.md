---
title: EmitAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d73c158fa9d7b5574e4f875b8d51e932e30041b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572243"
---
# <a name="emitassembly-method"></a><span data-ttu-id="0866d-102">EmitAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="0866d-102">EmitAssembly Method</span></span>
<span data-ttu-id="0866d-103">Tworzy zestaw.</span><span class="sxs-lookup"><span data-stu-id="0866d-103">Creates the assembly.</span></span> <span data-ttu-id="0866d-104">Wywołaj tę metodę po zamknięciu wszystkich innych plików z wyjątkiem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="0866d-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="0866d-105">Ta metoda zostanie wywołana podczas produkowania niepowiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="0866d-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0866d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0866d-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0866d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0866d-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0866d-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="0866d-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0866d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0866d-109">Return Value</span></span>  
 <span data-ttu-id="0866d-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0866d-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0866d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0866d-111">Requirements</span></span>  
 <span data-ttu-id="0866d-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="0866d-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0866d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0866d-113">See also</span></span>
- [<span data-ttu-id="0866d-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="0866d-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0866d-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0866d-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0866d-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="0866d-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
