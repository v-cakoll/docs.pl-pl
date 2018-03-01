---
title: "ExportTypeForwarder — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3fe418b1f8a5d5a6d3c2d36184ca76d5ef9989bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="b3f22-102">ExportTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3f22-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="b3f22-103">Dodaje usługę przesyłania dalej dla typu tabeli typu danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b3f22-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f22-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3f22-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3f22-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3f22-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="b3f22-106">Odwołanie do zestawu, do którego odwołuje się typ usługi przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="b3f22-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="b3f22-107">Pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="b3f22-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b3f22-108">`ComType`flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="b3f22-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="b3f22-109">Ta wartość może być przekazana do [DefineExportedType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="b3f22-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="b3f22-110">Odbiera token wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="b3f22-110">Receives the token of the exported type.</span></span> <span data-ttu-id="b3f22-111">Jest to konieczne tylko w przypadku emitowanie zagnieżdżone typy.</span><span class="sxs-lookup"><span data-stu-id="b3f22-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3f22-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b3f22-112">Return Value</span></span>  
 <span data-ttu-id="b3f22-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b3f22-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f22-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3f22-114">Requirements</span></span>  
 <span data-ttu-id="b3f22-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="b3f22-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f22-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3f22-116">See Also</span></span>  
 [<span data-ttu-id="b3f22-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3f22-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b3f22-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3f22-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b3f22-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="b3f22-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
