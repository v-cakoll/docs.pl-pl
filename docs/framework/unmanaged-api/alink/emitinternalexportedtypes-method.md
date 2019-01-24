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
ms.openlocfilehash: 68373e9277a9d87bba6941259588f25a92af90a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710550"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="50e46-102">EmitInternalExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="50e46-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="50e46-103">Emituje typów dodanych do zestawu.</span><span class="sxs-lookup"><span data-stu-id="50e46-103">Emits types added to the assembly.</span></span> <span data-ttu-id="50e46-104">Wywołaj tę metodę po wiadomo, że dodano typy wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="50e46-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e46-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="50e46-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50e46-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="50e46-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="50e46-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="50e46-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50e46-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50e46-108">Return Value</span></span>  
 <span data-ttu-id="50e46-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="50e46-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e46-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50e46-110">Requirements</span></span>  
 <span data-ttu-id="50e46-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="50e46-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e46-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50e46-112">See also</span></span>
- [<span data-ttu-id="50e46-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="50e46-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="50e46-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="50e46-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="50e46-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="50e46-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
