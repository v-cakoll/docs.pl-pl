---
title: SetNonAssemblyFlags — Metoda
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27ad89f1910bc7bb08a23c9fdb0d50828fb8b5e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741434"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="24cb5-102">SetNonAssemblyFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="24cb5-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="24cb5-103">Ustawia flagi, które nie są specyficzne dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="24cb5-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24cb5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24cb5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="24cb5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24cb5-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="24cb5-106">ALink flagi.</span><span class="sxs-lookup"><span data-stu-id="24cb5-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24cb5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24cb5-107">Return Value</span></span>  
 <span data-ttu-id="24cb5-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="24cb5-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24cb5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24cb5-109">Requirements</span></span>  
 <span data-ttu-id="24cb5-110">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="24cb5-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24cb5-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24cb5-111">See also</span></span>

- [<span data-ttu-id="24cb5-112">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="24cb5-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="24cb5-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="24cb5-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="24cb5-114">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="24cb5-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
