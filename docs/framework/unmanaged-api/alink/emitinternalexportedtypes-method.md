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
ms.openlocfilehash: d4b7064b0339825c29e4001bc35c4a604098468a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446500"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="82c9f-102">EmitInternalExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="82c9f-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="82c9f-103">Emits types added to the assembly.</span><span class="sxs-lookup"><span data-stu-id="82c9f-103">Emits types added to the assembly.</span></span> <span data-ttu-id="82c9f-104">Call this method after known internal types have been added.</span><span class="sxs-lookup"><span data-stu-id="82c9f-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c9f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="82c9f-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="82c9f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="82c9f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="82c9f-107">ID of assembly.</span><span class="sxs-lookup"><span data-stu-id="82c9f-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82c9f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="82c9f-108">Return Value</span></span>  
 <span data-ttu-id="82c9f-109">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="82c9f-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82c9f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82c9f-110">Requirements</span></span>  
 <span data-ttu-id="82c9f-111">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="82c9f-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c9f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82c9f-112">See also</span></span>

- [<span data-ttu-id="82c9f-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="82c9f-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="82c9f-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="82c9f-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="82c9f-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="82c9f-115">ALink API</span></span>](index.md)
