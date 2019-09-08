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
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777280"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="61e2d-102">ExportNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="61e2d-102">ExportNestedType Method</span></span>
<span data-ttu-id="61e2d-103">Określa typy zagnieżdżone jako możliwe do eksportowania.</span><span class="sxs-lookup"><span data-stu-id="61e2d-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="61e2d-104">[Metoda exporttype](exporttype-method.md) może również eksportować typy zagnieżdżone, ale ta metoda jest szybsza.</span><span class="sxs-lookup"><span data-stu-id="61e2d-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e2d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="61e2d-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="61e2d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="61e2d-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="61e2d-107">Identyfikator zestawu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="61e2d-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="61e2d-108">Token pliku lub zestaw pliku, który definiuje typ, który ma być możliwy do eksportu.</span><span class="sxs-lookup"><span data-stu-id="61e2d-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="61e2d-109">Typ token typu, który ma być możliwy do eksportu.</span><span class="sxs-lookup"><span data-stu-id="61e2d-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="61e2d-110">Token typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="61e2d-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="61e2d-111">W pełni kwalifikowana nazwa typu do eksportowania.</span><span class="sxs-lookup"><span data-stu-id="61e2d-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="61e2d-112">`ComType`flagi takie jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="61e2d-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="61e2d-113">Ta wartość może zostać przeniesiona do [metody DefineExportedType —](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="61e2d-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="61e2d-114">Odbiera token dla wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="61e2d-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61e2d-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="61e2d-115">Return Value</span></span>  
 <span data-ttu-id="61e2d-116">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="61e2d-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61e2d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61e2d-117">Requirements</span></span>  
 <span data-ttu-id="61e2d-118">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="61e2d-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e2d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61e2d-119">See also</span></span>

- [<span data-ttu-id="61e2d-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="61e2d-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="61e2d-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="61e2d-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="61e2d-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="61e2d-122">ALink API</span></span>](index.md)
