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
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179411"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="aa56f-102">ExportNestedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa56f-102">ExportNestedType Method</span></span>
<span data-ttu-id="aa56f-103">Określa typy zagnieżdżone jako możliwe do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="aa56f-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="aa56f-104">Metoda [ExportType](exporttype-method.md) można również eksportować zagnieżdżone typy, ale ta metoda jest szybsza.</span><span class="sxs-lookup"><span data-stu-id="aa56f-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa56f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa56f-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="aa56f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa56f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="aa56f-107">Identyfikator zestawu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="aa56f-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="aa56f-108">Token pliku lub montaż pliku, który definiuje typ, który ma być eksportowany.</span><span class="sxs-lookup"><span data-stu-id="aa56f-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="aa56f-109">Typ tokenu typu, który ma być eksportowany.</span><span class="sxs-lookup"><span data-stu-id="aa56f-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="aa56f-110">Token typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="aa56f-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="aa56f-111">W pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="aa56f-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="aa56f-112">`ComType`flagi, `tdPublic` takie `tdNested`jak lub .</span><span class="sxs-lookup"><span data-stu-id="aa56f-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="aa56f-113">Ta wartość może zostać przekazana do [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="aa56f-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="aa56f-114">Odbiera token dla eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="aa56f-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa56f-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa56f-115">Return Value</span></span>  
 <span data-ttu-id="aa56f-116">Zwraca S_OK, jeśli metoda powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="aa56f-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa56f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa56f-117">Requirements</span></span>  
 <span data-ttu-id="aa56f-118">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="aa56f-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa56f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa56f-119">See also</span></span>

- [<span data-ttu-id="aa56f-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa56f-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="aa56f-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa56f-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="aa56f-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="aa56f-122">ALink API</span></span>](index.md)
