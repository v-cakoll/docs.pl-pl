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
ms.openlocfilehash: 5c7ea671af5c6c725df136810bb8cf6610a6f83f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710342"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="3349a-102">ExportNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="3349a-102">ExportNestedType Method</span></span>
<span data-ttu-id="3349a-103">Określa typy zagnieżdżone jako eksportowalny.</span><span class="sxs-lookup"><span data-stu-id="3349a-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="3349a-104">[Exporttype — metoda](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) może również typy zagnieżdżone eksportu, ale ta metoda jest szybsza.</span><span class="sxs-lookup"><span data-stu-id="3349a-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3349a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3349a-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="3349a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3349a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3349a-107">Identyfikator zestawu, aby wyeksportować z.</span><span class="sxs-lookup"><span data-stu-id="3349a-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3349a-108">Token pliku lub zestawu plików, który definiuje typ, który ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="3349a-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="3349a-109">Typ tokenu typu ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="3349a-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="3349a-110">Token typie elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3349a-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="3349a-111">W pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="3349a-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3349a-112">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="3349a-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="3349a-113">Ta wartość może być przekazana do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3349a-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="3349a-114">Odbiera token dla eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="3349a-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3349a-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3349a-115">Return Value</span></span>  
 <span data-ttu-id="3349a-116">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3349a-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3349a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3349a-117">Requirements</span></span>  
 <span data-ttu-id="3349a-118">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="3349a-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3349a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3349a-119">See also</span></span>
- [<span data-ttu-id="3349a-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="3349a-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3349a-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3349a-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3349a-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="3349a-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
