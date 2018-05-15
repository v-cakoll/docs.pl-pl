---
title: ExportNestedType — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0afe4daa1c85f3e15addac55bdbe631d40e03f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="10b57-102">ExportNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="10b57-102">ExportNestedType Method</span></span>
<span data-ttu-id="10b57-103">Określa typy zagnieżdżone jako eksportowalny.</span><span class="sxs-lookup"><span data-stu-id="10b57-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="10b57-104">[ExportType — metoda](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) może również typy zagnieżdżone eksportu, ale ta metoda jest szybsza.</span><span class="sxs-lookup"><span data-stu-id="10b57-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10b57-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="10b57-105">Syntax</span></span>  
  
```  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="10b57-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="10b57-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="10b57-107">Identyfikator zestawu eksportu.</span><span class="sxs-lookup"><span data-stu-id="10b57-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="10b57-108">Token pliku lub zestawu plików, który definiuje typ, który ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="10b57-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="10b57-109">Typ tokenu typu ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="10b57-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="10b57-110">Token typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="10b57-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="10b57-111">Pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="10b57-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="10b57-112">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="10b57-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="10b57-113">Ta wartość może być przekazana do [DefineExportedType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="10b57-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="10b57-114">Odbiera token dla wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="10b57-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10b57-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="10b57-115">Return Value</span></span>  
 <span data-ttu-id="10b57-116">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="10b57-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10b57-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10b57-117">Requirements</span></span>  
 <span data-ttu-id="10b57-118">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="10b57-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b57-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10b57-119">See Also</span></span>  
 [<span data-ttu-id="10b57-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="10b57-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="10b57-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="10b57-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="10b57-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="10b57-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
