---
title: CloseAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94c1c083d010cd82fd9e9e2f02b23e81d88fedd5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116444"
---
# <a name="closeassembly-method"></a><span data-ttu-id="f43d7-102">CloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="f43d7-102">CloseAssembly Method</span></span>
<span data-ttu-id="f43d7-103">Kończenie znajdujących się w operacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="f43d7-103">Finalizes assembly operations.</span></span> <span data-ttu-id="f43d7-104">Tę metodę należy wywołać przed rozpoczęciem nowego zestawu lub modułu niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="f43d7-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f43d7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f43d7-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f43d7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f43d7-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f43d7-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="f43d7-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f43d7-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f43d7-108">Return Value</span></span>  
 <span data-ttu-id="f43d7-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f43d7-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f43d7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f43d7-110">Requirements</span></span>  
 <span data-ttu-id="f43d7-111">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="f43d7-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43d7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f43d7-112">See also</span></span>

- [<span data-ttu-id="f43d7-113">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="f43d7-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f43d7-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f43d7-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f43d7-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="f43d7-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
