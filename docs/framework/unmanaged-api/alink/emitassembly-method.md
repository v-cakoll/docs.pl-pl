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
ms.openlocfilehash: b0e6250987997b8d1c833b7b33a985900510fb03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742136"
---
# <a name="emitassembly-method"></a><span data-ttu-id="6521f-102">EmitAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="6521f-102">EmitAssembly Method</span></span>
<span data-ttu-id="6521f-103">Tworzy zestaw.</span><span class="sxs-lookup"><span data-stu-id="6521f-103">Creates the assembly.</span></span> <span data-ttu-id="6521f-104">Wywołaj tę metodę po zamknięciu wszystkich innych plików z wyjątkiem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="6521f-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="6521f-105">Ta metoda zostanie wywołana podczas produkowania niepowiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="6521f-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6521f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6521f-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6521f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6521f-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6521f-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="6521f-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6521f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6521f-109">Return Value</span></span>  
 <span data-ttu-id="6521f-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6521f-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6521f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6521f-111">Requirements</span></span>  
 <span data-ttu-id="6521f-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="6521f-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6521f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6521f-113">See also</span></span>

- [<span data-ttu-id="6521f-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="6521f-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6521f-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6521f-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6521f-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="6521f-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
