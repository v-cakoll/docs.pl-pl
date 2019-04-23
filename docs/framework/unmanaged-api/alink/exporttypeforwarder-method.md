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
ms.openlocfilehash: 5bdf9fb50fe06141df6f3818c784588b9e2138af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212027"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="5c043-102">ExportTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c043-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="5c043-103">Dodaje typ usługi przesyłania dalej do tabeli typu danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5c043-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c043-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c043-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c043-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c043-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="5c043-106">Odwołanie do zestawu, do którego odwołuje się typ usługi przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="5c043-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="5c043-107">W pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="5c043-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5c043-108">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="5c043-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="5c043-109">Ta wartość może być przekazana do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c043-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="5c043-110">Odbiera token wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="5c043-110">Receives the token of the exported type.</span></span> <span data-ttu-id="5c043-111">Jest to niezbędne tylko w przypadku emitowania zagnieżdżone typy.</span><span class="sxs-lookup"><span data-stu-id="5c043-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c043-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5c043-112">Return Value</span></span>  
 <span data-ttu-id="5c043-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5c043-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c043-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c043-114">Requirements</span></span>  
 <span data-ttu-id="5c043-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="5c043-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c043-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c043-116">See also</span></span>

- [<span data-ttu-id="5c043-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c043-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="5c043-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c043-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="5c043-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="5c043-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
