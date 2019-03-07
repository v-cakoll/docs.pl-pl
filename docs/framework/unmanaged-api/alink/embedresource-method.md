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
ms.openlocfilehash: ffcd389f9b9e2e113fc45d2961a92790f4c57ae8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478053"
---
# <a name="embedresource-method"></a><span data-ttu-id="23128-102">EmbedResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="23128-102">EmbedResource Method</span></span>
<span data-ttu-id="23128-103">Deklaruje zasobu osadzonego.</span><span class="sxs-lookup"><span data-stu-id="23128-103">Declares an embedded resource.</span></span> <span data-ttu-id="23128-104">Ta metoda faktycznie osadzaj zasobu.</span><span class="sxs-lookup"><span data-stu-id="23128-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23128-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="23128-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="23128-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="23128-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="23128-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="23128-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="23128-108">Plik tokenu lub zestawu identyfikator pliku, który zawiera zasób.</span><span class="sxs-lookup"><span data-stu-id="23128-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="23128-109">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="23128-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="23128-110">Przesunięcie zasobach RVA.</span><span class="sxs-lookup"><span data-stu-id="23128-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="23128-111">Ułatwienia dostępu flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="23128-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="23128-112">Te flagi mogą być przekazywane do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="23128-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23128-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="23128-113">Return Value</span></span>  
 <span data-ttu-id="23128-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="23128-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23128-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23128-115">Requirements</span></span>  
 <span data-ttu-id="23128-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="23128-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23128-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23128-117">See also</span></span>
- [<span data-ttu-id="23128-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="23128-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="23128-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="23128-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="23128-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="23128-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
