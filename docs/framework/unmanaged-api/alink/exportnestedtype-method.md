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
ms.openlocfilehash: fded6b95144d4088a2abc8dfcc4ef8eda331c34f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438425"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="03e80-102">ExportNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="03e80-102">ExportNestedType Method</span></span>
<span data-ttu-id="03e80-103">Określa typy zagnieżdżone jako możliwe do eksportowania.</span><span class="sxs-lookup"><span data-stu-id="03e80-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="03e80-104">[Metoda exporttype](exporttype-method.md) może również eksportować typy zagnieżdżone, ale ta metoda jest szybsza.</span><span class="sxs-lookup"><span data-stu-id="03e80-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e80-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="03e80-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="03e80-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="03e80-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="03e80-107">Identyfikator zestawu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="03e80-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="03e80-108">Token pliku lub zestaw pliku, który definiuje typ, który ma być możliwy do eksportu.</span><span class="sxs-lookup"><span data-stu-id="03e80-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="03e80-109">Typ token typu, który ma być możliwy do eksportu.</span><span class="sxs-lookup"><span data-stu-id="03e80-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="03e80-110">Token typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="03e80-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="03e80-111">W pełni kwalifikowana nazwa typu do eksportowania.</span><span class="sxs-lookup"><span data-stu-id="03e80-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="03e80-112">`ComType` flagi, takie jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="03e80-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="03e80-113">Ta wartość może zostać przeniesiona do [metody DefineExportedType —](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="03e80-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="03e80-114">Odbiera token dla wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="03e80-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03e80-115">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="03e80-115">Return Value</span></span>  
 <span data-ttu-id="03e80-116">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="03e80-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e80-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03e80-117">Requirements</span></span>  
 <span data-ttu-id="03e80-118">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="03e80-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e80-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03e80-119">See also</span></span>

- [<span data-ttu-id="03e80-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="03e80-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="03e80-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="03e80-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="03e80-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="03e80-122">ALink API</span></span>](index.md)
