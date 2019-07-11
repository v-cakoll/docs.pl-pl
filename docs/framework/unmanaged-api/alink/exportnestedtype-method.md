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
ms.openlocfilehash: 7dfaedad48291ac09f6959bc7b314ae0d9da76e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742044"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="40db0-102">ExportNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="40db0-102">ExportNestedType Method</span></span>
<span data-ttu-id="40db0-103">Określa typy zagnieżdżone jako eksportowalny.</span><span class="sxs-lookup"><span data-stu-id="40db0-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="40db0-104">[Exporttype — metoda](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) może również typy zagnieżdżone eksportu, ale ta metoda jest szybsza.</span><span class="sxs-lookup"><span data-stu-id="40db0-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40db0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="40db0-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="40db0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="40db0-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="40db0-107">Identyfikator zestawu, aby wyeksportować z.</span><span class="sxs-lookup"><span data-stu-id="40db0-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="40db0-108">Token pliku lub zestawu plików, który definiuje typ, który ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="40db0-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="40db0-109">Typ tokenu typu ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="40db0-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="40db0-110">Token typie elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="40db0-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="40db0-111">W pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="40db0-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="40db0-112">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="40db0-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="40db0-113">Ta wartość może być przekazana do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="40db0-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="40db0-114">Odbiera token dla eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="40db0-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40db0-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40db0-115">Return Value</span></span>  
 <span data-ttu-id="40db0-116">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="40db0-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40db0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40db0-117">Requirements</span></span>  
 <span data-ttu-id="40db0-118">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="40db0-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40db0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40db0-119">See also</span></span>

- [<span data-ttu-id="40db0-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="40db0-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="40db0-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="40db0-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="40db0-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="40db0-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
