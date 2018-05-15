---
title: PreCloseAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82421fa83a6f0d24492d70f961e731b679c25728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="precloseassembly-method"></a><span data-ttu-id="c6a8e-102">PreCloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6a8e-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="c6a8e-103">Zamyka plik zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6a8e-103">Closes the assembly file.</span></span> <span data-ttu-id="c6a8e-104">Tę metodę można wywołać po zamknięciu wszystkich innych plików, ale przed zamknięciem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6a8e-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="c6a8e-105">Nie wywołuj tej metody dla modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="c6a8e-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6a8e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6a8e-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6a8e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6a8e-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c6a8e-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6a8e-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6a8e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c6a8e-109">Return Value</span></span>  
 <span data-ttu-id="c6a8e-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c6a8e-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6a8e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6a8e-111">Requirements</span></span>  
 <span data-ttu-id="c6a8e-112">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="c6a8e-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a8e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6a8e-113">See Also</span></span>  
 [<span data-ttu-id="c6a8e-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6a8e-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c6a8e-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6a8e-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c6a8e-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="c6a8e-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
