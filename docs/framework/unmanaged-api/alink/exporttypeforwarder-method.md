---
title: ExportTypeForwarder — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03949fb52d23e3b0f107f9f1d5208208369c3960
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574618"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="f73e9-102">ExportTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="f73e9-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="f73e9-103">Dodaje typ usługi przesyłania dalej do tabeli typu danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f73e9-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f73e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f73e9-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f73e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f73e9-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="f73e9-106">Odwołanie do zestawu, do którego odwołuje się typ usługi przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="f73e9-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="f73e9-107">W pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="f73e9-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f73e9-108">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="f73e9-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="f73e9-109">Ta wartość może być przekazana do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f73e9-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="f73e9-110">Odbiera token wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="f73e9-110">Receives the token of the exported type.</span></span> <span data-ttu-id="f73e9-111">Jest to niezbędne tylko w przypadku emitowania zagnieżdżone typy.</span><span class="sxs-lookup"><span data-stu-id="f73e9-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f73e9-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f73e9-112">Return Value</span></span>  
 <span data-ttu-id="f73e9-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f73e9-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f73e9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f73e9-114">Requirements</span></span>  
 <span data-ttu-id="f73e9-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="f73e9-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f73e9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f73e9-116">See also</span></span>
- [<span data-ttu-id="f73e9-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="f73e9-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f73e9-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f73e9-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f73e9-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="f73e9-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
