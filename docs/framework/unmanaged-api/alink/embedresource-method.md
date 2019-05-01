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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790055"
---
# <a name="embedresource-method"></a><span data-ttu-id="cfdec-102">EmbedResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="cfdec-102">EmbedResource Method</span></span>
<span data-ttu-id="cfdec-103">Deklaruje zasobu osadzonego.</span><span class="sxs-lookup"><span data-stu-id="cfdec-103">Declares an embedded resource.</span></span> <span data-ttu-id="cfdec-104">Ta metoda faktycznie osadzaj zasobu.</span><span class="sxs-lookup"><span data-stu-id="cfdec-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfdec-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfdec-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfdec-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfdec-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="cfdec-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="cfdec-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="cfdec-108">Plik tokenu lub zestawu identyfikator pliku, który zawiera zasób.</span><span class="sxs-lookup"><span data-stu-id="cfdec-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="cfdec-109">Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="cfdec-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="cfdec-110">Przesunięcie zasobach RVA.</span><span class="sxs-lookup"><span data-stu-id="cfdec-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cfdec-111">Ułatwienia dostępu flagi, takich jak `mrPublic` i `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="cfdec-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="cfdec-112">Te flagi mogą być przekazywane do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="cfdec-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfdec-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cfdec-113">Return Value</span></span>  
 <span data-ttu-id="cfdec-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cfdec-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfdec-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfdec-115">Requirements</span></span>  
 <span data-ttu-id="cfdec-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="cfdec-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdec-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfdec-117">See also</span></span>

- [<span data-ttu-id="cfdec-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfdec-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="cfdec-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfdec-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="cfdec-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="cfdec-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
