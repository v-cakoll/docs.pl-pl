---
title: EmbedResource — Metoda
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb1fc266c8451953c8b6a9c686f4a1c1951966e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405401"
---
# <a name="embedresource-method"></a><span data-ttu-id="beec2-102">EmbedResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="beec2-102">EmbedResource Method</span></span>
<span data-ttu-id="beec2-103">Deklaruje osadzony zasób.</span><span class="sxs-lookup"><span data-stu-id="beec2-103">Declares an embedded resource.</span></span> <span data-ttu-id="beec2-104">Ta metoda nie faktycznie osadzanie zasobu.</span><span class="sxs-lookup"><span data-stu-id="beec2-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beec2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="beec2-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="beec2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="beec2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="beec2-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="beec2-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="beec2-108">Identyfikator tokenu lub zestawu pliku, który zawiera zasób pliku.</span><span class="sxs-lookup"><span data-stu-id="beec2-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="beec2-109">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="beec2-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="beec2-110">Przesunięcie zasobu z adres RVA.</span><span class="sxs-lookup"><span data-stu-id="beec2-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="beec2-111">Dostępność flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="beec2-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="beec2-112">Te flagi mogą zostać przekazane do [DefineExportedType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="beec2-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="beec2-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="beec2-113">Return Value</span></span>  
 <span data-ttu-id="beec2-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="beec2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beec2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="beec2-115">Requirements</span></span>  
 <span data-ttu-id="beec2-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="beec2-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beec2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="beec2-117">See Also</span></span>  
 [<span data-ttu-id="beec2-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="beec2-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="beec2-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="beec2-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="beec2-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="beec2-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
