---
title: "ExportTypeForwarder — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportTypeForwarder
helpviewer_keywords: ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f117d64673729113d917d700e3a26f9723b5a6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="1299f-102">ExportTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="1299f-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="1299f-103">Dodaje usługę przesyłania dalej dla typu tabeli typu danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1299f-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1299f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1299f-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1299f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1299f-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="1299f-106">Odwołanie do zestawu, do którego odwołuje się typ usługi przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="1299f-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="1299f-107">Pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="1299f-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1299f-108">`ComType`flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="1299f-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="1299f-109">Ta wartość może być przekazana do [DefineExportedType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="1299f-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="1299f-110">Odbiera token wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="1299f-110">Receives the token of the exported type.</span></span> <span data-ttu-id="1299f-111">Jest to konieczne tylko w przypadku emitowanie zagnieżdżone typy.</span><span class="sxs-lookup"><span data-stu-id="1299f-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1299f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1299f-112">Return Value</span></span>  
 <span data-ttu-id="1299f-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1299f-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1299f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1299f-114">Requirements</span></span>  
 <span data-ttu-id="1299f-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="1299f-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1299f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1299f-116">See Also</span></span>  
 [<span data-ttu-id="1299f-117">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="1299f-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1299f-118">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="1299f-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1299f-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="1299f-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
