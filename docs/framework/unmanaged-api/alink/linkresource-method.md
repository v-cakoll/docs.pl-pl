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
ms.openlocfilehash: 6e851c1bd56c0e9ece02fb06c0dcd9975a5b02ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079439"
---
# <a name="linkresource-method"></a><span data-ttu-id="39c4b-102">LinkResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="39c4b-102">LinkResource Method</span></span>
<span data-ttu-id="39c4b-103">Linki w zasobie.</span><span class="sxs-lookup"><span data-stu-id="39c4b-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c4b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39c4b-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="39c4b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39c4b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="39c4b-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="39c4b-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="39c4b-107">Nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="39c4b-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="39c4b-108">Opcjonalne nową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="39c4b-108">Optional new file name.</span></span> <span data-ttu-id="39c4b-109">Jeśli innych niż NULL, `pszFileName` zostaną skopiowane do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="39c4b-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="39c4b-110">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="39c4b-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="39c4b-111">Ułatwienia dostępu flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="39c4b-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="39c4b-112">Ten parametr może być przekazana do [definemanifestresource — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="39c4b-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39c4b-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="39c4b-113">Return Value</span></span>  
 <span data-ttu-id="39c4b-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="39c4b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c4b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39c4b-115">Requirements</span></span>  
 <span data-ttu-id="39c4b-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="39c4b-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c4b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39c4b-117">See also</span></span>

- [<span data-ttu-id="39c4b-118">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="39c4b-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="39c4b-119">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="39c4b-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="39c4b-120">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="39c4b-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
