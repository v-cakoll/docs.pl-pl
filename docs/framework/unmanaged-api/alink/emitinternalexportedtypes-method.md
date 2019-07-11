---
title: EmitInternalExportedTypes — Metoda
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15174480c4345f2514572701a5525f0f192ad120
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742104"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="d1ee6-102">EmitInternalExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1ee6-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="d1ee6-103">Emituje typów dodanych do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d1ee6-103">Emits types added to the assembly.</span></span> <span data-ttu-id="d1ee6-104">Wywołaj tę metodę po wiadomo, że dodano typy wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="d1ee6-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ee6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1ee6-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1ee6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1ee6-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d1ee6-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="d1ee6-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1ee6-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1ee6-108">Return Value</span></span>  
 <span data-ttu-id="d1ee6-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d1ee6-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1ee6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1ee6-110">Requirements</span></span>  
 <span data-ttu-id="d1ee6-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="d1ee6-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ee6-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1ee6-112">See also</span></span>

- [<span data-ttu-id="d1ee6-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1ee6-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d1ee6-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1ee6-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d1ee6-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="d1ee6-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
