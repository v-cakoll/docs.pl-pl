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
ms.openlocfilehash: 68698aab0fd0872c6e6f67e4ec531ab0226e784f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401956"
---
# <a name="closeassembly-method"></a><span data-ttu-id="79027-102">CloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="79027-102">CloseAssembly Method</span></span>
<span data-ttu-id="79027-103">Kończenie znajdujących się w zestawie operacji.</span><span class="sxs-lookup"><span data-stu-id="79027-103">Finalizes assembly operations.</span></span> <span data-ttu-id="79027-104">Tę metodę należy wywołać przed rozpoczęciem nowego zestawu lub modułu niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="79027-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79027-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="79027-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79027-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79027-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="79027-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="79027-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79027-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="79027-108">Return Value</span></span>  
 <span data-ttu-id="79027-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="79027-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79027-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79027-110">Requirements</span></span>  
 <span data-ttu-id="79027-111">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="79027-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79027-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79027-112">See Also</span></span>  
 [<span data-ttu-id="79027-113">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="79027-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="79027-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="79027-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="79027-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="79027-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
