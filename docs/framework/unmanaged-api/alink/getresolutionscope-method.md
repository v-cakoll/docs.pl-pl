---
title: GetResolutionScope — Metoda
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e67a71c25c0ae8ee7c54fae2e38d1116a5d92eff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402592"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="65511-102">GetResolutionScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="65511-102">GetResolutionScope Method</span></span>
<span data-ttu-id="65511-103">Pobiera zakres danego typu.</span><span class="sxs-lookup"><span data-stu-id="65511-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65511-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65511-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65511-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65511-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="65511-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="65511-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="65511-107">Plik, który wymaga odwołania.</span><span class="sxs-lookup"><span data-stu-id="65511-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="65511-108">Token pliku tego typu jest zdefiniowany w, zwykle pobrany za pomocą [ImportFile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="65511-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="65511-109">Odbiera zestawu lub odwołania do modułu.</span><span class="sxs-lookup"><span data-stu-id="65511-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65511-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="65511-110">Return Value</span></span>  
 <span data-ttu-id="65511-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="65511-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65511-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65511-112">Requirements</span></span>  
 <span data-ttu-id="65511-113">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="65511-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65511-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65511-114">See Also</span></span>  
 [<span data-ttu-id="65511-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="65511-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="65511-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="65511-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="65511-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="65511-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
