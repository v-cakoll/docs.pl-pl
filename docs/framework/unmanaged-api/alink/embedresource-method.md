---
title: "EmbedResource — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmbedResource
- EmbedResource
api_location: alink.dll
api_type: COM
f1_keywords: EmbedResource
helpviewer_keywords: EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 98dbd32452184bf4f832bd66ffebb0fcf3d5bb0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="embedresource-method"></a><span data-ttu-id="4795a-102">EmbedResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="4795a-102">EmbedResource Method</span></span>
<span data-ttu-id="4795a-103">Deklaruje osadzony zasób.</span><span class="sxs-lookup"><span data-stu-id="4795a-103">Declares an embedded resource.</span></span> <span data-ttu-id="4795a-104">Ta metoda nie faktycznie osadzanie zasobu.</span><span class="sxs-lookup"><span data-stu-id="4795a-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4795a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4795a-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4795a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4795a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4795a-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="4795a-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4795a-108">Identyfikator tokenu lub zestawu pliku, który zawiera zasób pliku.</span><span class="sxs-lookup"><span data-stu-id="4795a-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="4795a-109">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="4795a-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="4795a-110">Przesunięcie zasobu z adres RVA.</span><span class="sxs-lookup"><span data-stu-id="4795a-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4795a-111">Dostępność flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="4795a-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="4795a-112">Te flagi mogą zostać przekazane do [DefineExportedType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="4795a-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4795a-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4795a-113">Return Value</span></span>  
 <span data-ttu-id="4795a-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="4795a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4795a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4795a-115">Requirements</span></span>  
 <span data-ttu-id="4795a-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="4795a-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4795a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4795a-117">See Also</span></span>  
 [<span data-ttu-id="4795a-118">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="4795a-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="4795a-119">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="4795a-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="4795a-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="4795a-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
