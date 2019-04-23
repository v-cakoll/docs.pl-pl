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
ms.openlocfilehash: bf7b54ab7a2318e8194bf39dbe41b864633ddb43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212914"
---
# <a name="emitassembly-method"></a><span data-ttu-id="10781-102">EmitAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="10781-102">EmitAssembly Method</span></span>
<span data-ttu-id="10781-103">Tworzy zestaw.</span><span class="sxs-lookup"><span data-stu-id="10781-103">Creates the assembly.</span></span> <span data-ttu-id="10781-104">Wywołaj tę metodę po zamknięciu wszystkich innych plików z wyjątkiem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="10781-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="10781-105">Ta metoda zostanie wywołana podczas produkowania niepowiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="10781-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10781-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="10781-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="10781-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="10781-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="10781-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="10781-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10781-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="10781-109">Return Value</span></span>  
 <span data-ttu-id="10781-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="10781-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10781-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10781-111">Requirements</span></span>  
 <span data-ttu-id="10781-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="10781-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10781-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10781-113">See also</span></span>

- [<span data-ttu-id="10781-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="10781-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="10781-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="10781-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="10781-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="10781-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
