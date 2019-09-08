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
ms.openlocfilehash: a2bfb43002b79fd3e499272b87756bdc3ab0b589
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787342"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="6cb0f-102">GetResolutionScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="6cb0f-102">GetResolutionScope Method</span></span>
<span data-ttu-id="6cb0f-103">Pobiera zakres danego typu.</span><span class="sxs-lookup"><span data-stu-id="6cb0f-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6cb0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cb0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cb0f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6cb0f-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="6cb0f-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6cb0f-107">Plik, który jest wymagany do odwołania.</span><span class="sxs-lookup"><span data-stu-id="6cb0f-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="6cb0f-108">Token pliku, który jest zdefiniowany w, zazwyczaj pobierany przy użyciu [metody ImportFile —](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="6cb0f-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="6cb0f-109">Odbiera odwołanie zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="6cb0f-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cb0f-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6cb0f-110">Return Value</span></span>  
 <span data-ttu-id="6cb0f-111">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6cb0f-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cb0f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cb0f-112">Requirements</span></span>  
 <span data-ttu-id="6cb0f-113">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="6cb0f-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb0f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cb0f-114">See also</span></span>

- [<span data-ttu-id="6cb0f-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cb0f-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6cb0f-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cb0f-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6cb0f-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="6cb0f-117">ALink API</span></span>](index.md)
