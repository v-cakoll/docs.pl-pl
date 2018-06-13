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
ms.openlocfilehash: 1cd1c077a8f2a5fe3b2b46c2e1da2e92b5a797a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402060"
---
# <a name="emitassembly-method"></a><span data-ttu-id="1fe18-102">EmitAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="1fe18-102">EmitAssembly Method</span></span>
<span data-ttu-id="1fe18-103">Tworzy zestaw.</span><span class="sxs-lookup"><span data-stu-id="1fe18-103">Creates the assembly.</span></span> <span data-ttu-id="1fe18-104">Tę metodę można wywołać po zamknięciu wszystkich innych plików z wyjątkiem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="1fe18-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="1fe18-105">Ta metoda zostanie wywołana podczas produkowania niezwiązanego modułów.</span><span class="sxs-lookup"><span data-stu-id="1fe18-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe18-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fe18-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fe18-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fe18-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1fe18-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="1fe18-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fe18-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1fe18-109">Return Value</span></span>  
 <span data-ttu-id="1fe18-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1fe18-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fe18-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1fe18-111">Requirements</span></span>  
 <span data-ttu-id="1fe18-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="1fe18-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe18-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fe18-113">See Also</span></span>  
 [<span data-ttu-id="1fe18-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="1fe18-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1fe18-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1fe18-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1fe18-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="1fe18-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
