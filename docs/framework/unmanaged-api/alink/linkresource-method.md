---
title: LinkResource — Metoda
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61f82a34c287c62e1180c9c6bbe090914763afa3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479093"
---
# <a name="linkresource-method"></a><span data-ttu-id="8b715-102">LinkResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b715-102">LinkResource Method</span></span>
<span data-ttu-id="8b715-103">Linki w zasobie.</span><span class="sxs-lookup"><span data-stu-id="8b715-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b715-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b715-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b715-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b715-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8b715-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="8b715-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="8b715-107">Nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="8b715-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="8b715-108">Opcjonalne nową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="8b715-108">Optional new file name.</span></span> <span data-ttu-id="8b715-109">Jeśli innych niż NULL, `pszFileName` zostaną skopiowane do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="8b715-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="8b715-110">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="8b715-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8b715-111">Ułatwienia dostępu flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="8b715-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="8b715-112">Ten parametr może być przekazana do [definemanifestresource — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="8b715-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b715-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b715-113">Return Value</span></span>  
 <span data-ttu-id="8b715-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8b715-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b715-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b715-115">Requirements</span></span>  
 <span data-ttu-id="8b715-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="8b715-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b715-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b715-117">See also</span></span>
- [<span data-ttu-id="8b715-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b715-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8b715-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b715-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8b715-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="8b715-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
