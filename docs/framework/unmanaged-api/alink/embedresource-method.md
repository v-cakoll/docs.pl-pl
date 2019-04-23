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
ms.openlocfilehash: ef7d6272c04c3edab8ef652bcb2759861ff2b982
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129574"
---
# <a name="embedresource-method"></a><span data-ttu-id="e164a-102">EmbedResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="e164a-102">EmbedResource Method</span></span>
<span data-ttu-id="e164a-103">Deklaruje zasobu osadzonego.</span><span class="sxs-lookup"><span data-stu-id="e164a-103">Declares an embedded resource.</span></span> <span data-ttu-id="e164a-104">Ta metoda faktycznie osadzaj zasobu.</span><span class="sxs-lookup"><span data-stu-id="e164a-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e164a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e164a-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e164a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e164a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e164a-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="e164a-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e164a-108">Plik tokenu lub zestawu identyfikator pliku, który zawiera zasób.</span><span class="sxs-lookup"><span data-stu-id="e164a-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="e164a-109">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="e164a-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="e164a-110">Przesunięcie zasobach RVA.</span><span class="sxs-lookup"><span data-stu-id="e164a-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e164a-111">Ułatwienia dostępu flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="e164a-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="e164a-112">Te flagi mogą być przekazywane do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="e164a-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e164a-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e164a-113">Return Value</span></span>  
 <span data-ttu-id="e164a-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e164a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e164a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e164a-115">Requirements</span></span>  
 <span data-ttu-id="e164a-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="e164a-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e164a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e164a-117">See also</span></span>

- [<span data-ttu-id="e164a-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="e164a-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e164a-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e164a-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e164a-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="e164a-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
