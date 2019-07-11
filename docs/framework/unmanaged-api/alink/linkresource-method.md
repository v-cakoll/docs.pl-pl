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
ms.openlocfilehash: 335d80255f7a3f5a22e8a69aa91c9e5b0843ea1e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741591"
---
# <a name="linkresource-method"></a><span data-ttu-id="679a7-102">LinkResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="679a7-102">LinkResource Method</span></span>
<span data-ttu-id="679a7-103">Linki w zasobie.</span><span class="sxs-lookup"><span data-stu-id="679a7-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="679a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="679a7-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="679a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="679a7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="679a7-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="679a7-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="679a7-107">Nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="679a7-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="679a7-108">Opcjonalne nową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="679a7-108">Optional new file name.</span></span> <span data-ttu-id="679a7-109">Jeśli innych niż NULL, `pszFileName` zostaną skopiowane do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="679a7-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="679a7-110">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="679a7-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="679a7-111">Ułatwienia dostępu flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="679a7-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="679a7-112">Ten parametr może być przekazana do [definemanifestresource — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="679a7-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="679a7-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="679a7-113">Return Value</span></span>  
 <span data-ttu-id="679a7-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="679a7-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="679a7-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="679a7-115">Requirements</span></span>  
 <span data-ttu-id="679a7-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="679a7-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679a7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="679a7-117">See also</span></span>

- [<span data-ttu-id="679a7-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="679a7-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="679a7-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="679a7-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="679a7-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="679a7-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
