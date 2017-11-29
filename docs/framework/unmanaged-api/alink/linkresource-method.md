---
title: "LinkResource — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.LinkResource
api_location: alink.dll
api_type: COM
f1_keywords: LinkResource
helpviewer_keywords: LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8cb1f985c1d735fa20507ab90d478e97025c9e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-method"></a><span data-ttu-id="e51c1-102">LinkResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="e51c1-102">LinkResource Method</span></span>
<span data-ttu-id="e51c1-103">Łącza w zasobie.</span><span class="sxs-lookup"><span data-stu-id="e51c1-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e51c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e51c1-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e51c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e51c1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e51c1-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="e51c1-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="e51c1-107">Nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="e51c1-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="e51c1-108">Opcjonalne nową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="e51c1-108">Optional new file name.</span></span> <span data-ttu-id="e51c1-109">Jeśli inną niż NULL, `pszFileName` zostaną skopiowane do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="e51c1-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="e51c1-110">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="e51c1-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e51c1-111">Dostępność flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="e51c1-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="e51c1-112">Ten parametr może być przekazana do [DefineManifestResource — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="e51c1-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e51c1-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e51c1-113">Return Value</span></span>  
 <span data-ttu-id="e51c1-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e51c1-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e51c1-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e51c1-115">Requirements</span></span>  
 <span data-ttu-id="e51c1-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="e51c1-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51c1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e51c1-117">See Also</span></span>  
 [<span data-ttu-id="e51c1-118">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="e51c1-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e51c1-119">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="e51c1-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e51c1-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="e51c1-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
