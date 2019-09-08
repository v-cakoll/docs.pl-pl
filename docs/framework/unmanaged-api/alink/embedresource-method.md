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
ms.openlocfilehash: 5f6140e5f85a7ee21773c96a5abdccadaddab92e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777458"
---
# <a name="embedresource-method"></a><span data-ttu-id="8bc35-102">EmbedResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="8bc35-102">EmbedResource Method</span></span>
<span data-ttu-id="8bc35-103">Deklaruje zasób osadzony.</span><span class="sxs-lookup"><span data-stu-id="8bc35-103">Declares an embedded resource.</span></span> <span data-ttu-id="8bc35-104">Ta metoda nie osadza zasobów w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="8bc35-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc35-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bc35-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bc35-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bc35-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8bc35-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="8bc35-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8bc35-108">Token pliku lub identyfikator zestawu pliku zawierającego zasób.</span><span class="sxs-lookup"><span data-stu-id="8bc35-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="8bc35-109">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="8bc35-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="8bc35-110">Przesunięcie zasobu z adresu RVA.</span><span class="sxs-lookup"><span data-stu-id="8bc35-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8bc35-111">Flagi dostępności, takie `mrPublic` jak `mrPrivate`i.</span><span class="sxs-lookup"><span data-stu-id="8bc35-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="8bc35-112">Flagi te mogą być przesyłane do [metody DefineExportedType —](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="8bc35-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bc35-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8bc35-113">Return Value</span></span>  
 <span data-ttu-id="8bc35-114">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8bc35-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc35-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bc35-115">Requirements</span></span>  
 <span data-ttu-id="8bc35-116">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="8bc35-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc35-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bc35-117">See also</span></span>

- [<span data-ttu-id="8bc35-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="8bc35-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8bc35-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8bc35-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8bc35-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="8bc35-120">ALink API</span></span>](index.md)
