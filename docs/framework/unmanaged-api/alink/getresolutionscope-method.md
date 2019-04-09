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
ms.openlocfilehash: 6c6d298c84b801b87832c56026b05f647cb5a9dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135183"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="c7c50-102">GetResolutionScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7c50-102">GetResolutionScope Method</span></span>
<span data-ttu-id="c7c50-103">Pobiera zakres danego typu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7c50-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7c50-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7c50-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7c50-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c7c50-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c7c50-107">Plik, który wymaga odwołania.</span><span class="sxs-lookup"><span data-stu-id="c7c50-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="c7c50-108">Token pliku tego typu jest zdefiniowany w, zwykle pobierane za pomocą [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c7c50-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="c7c50-109">Odbiera zestawu lub odwołanie do modułu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7c50-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c7c50-110">Return Value</span></span>  
 <span data-ttu-id="c7c50-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c7c50-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7c50-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7c50-112">Requirements</span></span>  
 <span data-ttu-id="c7c50-113">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="c7c50-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c50-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7c50-114">See also</span></span>

- [<span data-ttu-id="c7c50-115">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7c50-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c7c50-116">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7c50-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c7c50-117">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="c7c50-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
