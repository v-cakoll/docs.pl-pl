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
ms.openlocfilehash: 763b7a776007c2ce8dac42c6a5f7f00f6eb58a10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776945"
---
# <a name="linkresource-method"></a><span data-ttu-id="28fd7-102">LinkResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="28fd7-102">LinkResource Method</span></span>
<span data-ttu-id="28fd7-103">Linki w zasobie.</span><span class="sxs-lookup"><span data-stu-id="28fd7-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28fd7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28fd7-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="28fd7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28fd7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="28fd7-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="28fd7-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="28fd7-107">Nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="28fd7-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="28fd7-108">Opcjonalna nazwa nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="28fd7-108">Optional new file name.</span></span> <span data-ttu-id="28fd7-109">Jeśli wartość nie jest równa null, `pszFileName` zostanie skopiowana do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="28fd7-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="28fd7-110">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="28fd7-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="28fd7-111">Flagi dostępności, takie `mrPublic` jak `mrPrivate`i.</span><span class="sxs-lookup"><span data-stu-id="28fd7-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="28fd7-112">Ten parametr może być przesłany do [metody DefineManifestResource —](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="28fd7-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28fd7-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="28fd7-113">Return Value</span></span>  
 <span data-ttu-id="28fd7-114">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="28fd7-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28fd7-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28fd7-115">Requirements</span></span>  
 <span data-ttu-id="28fd7-116">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="28fd7-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28fd7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28fd7-117">See also</span></span>

- [<span data-ttu-id="28fd7-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="28fd7-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="28fd7-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="28fd7-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="28fd7-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="28fd7-120">ALink API</span></span>](index.md)
