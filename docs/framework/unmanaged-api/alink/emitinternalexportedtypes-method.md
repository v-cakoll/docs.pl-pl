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
ms.openlocfilehash: c196bcc159b18b9dc04329d817ebe16e07bb8bb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790016"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="cdc74-102">EmitInternalExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="cdc74-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="cdc74-103">Emituje typów dodanych do zestawu.</span><span class="sxs-lookup"><span data-stu-id="cdc74-103">Emits types added to the assembly.</span></span> <span data-ttu-id="cdc74-104">Wywołaj tę metodę po wiadomo, że dodano typy wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="cdc74-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc74-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdc74-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdc74-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdc74-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="cdc74-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="cdc74-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdc74-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cdc74-108">Return Value</span></span>  
 <span data-ttu-id="cdc74-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cdc74-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdc74-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cdc74-110">Requirements</span></span>  
 <span data-ttu-id="cdc74-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="cdc74-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc74-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdc74-112">See also</span></span>

- [<span data-ttu-id="cdc74-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cdc74-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="cdc74-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="cdc74-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="cdc74-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="cdc74-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
