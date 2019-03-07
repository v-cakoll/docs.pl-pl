---
title: ExportNestedTypeForwarder — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ed615ea641293f8ea3fdf962e3f84d602934df60
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494691"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="69c70-102">ExportNestedTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="69c70-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="69c70-103">Dodaje typ usługi przesyłania dalej dla typu zagnieżdżonego do tabeli typu danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="69c70-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69c70-104">Syntax</span></span>  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="69c70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69c70-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="69c70-106">Identyfikator zestawu, aby wyeksportować z.</span><span class="sxs-lookup"><span data-stu-id="69c70-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="69c70-107">Identyfikator tokenu lub zestawu w pliku, który definiuje typ pliku.</span><span class="sxs-lookup"><span data-stu-id="69c70-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="69c70-108">Token dla typu.</span><span class="sxs-lookup"><span data-stu-id="69c70-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="69c70-109">Token typie elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="69c70-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="69c70-110">W pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="69c70-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="69c70-111">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="69c70-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="69c70-112">Odbiera token typu eksportu.</span><span class="sxs-lookup"><span data-stu-id="69c70-112">Receives token of export type.</span></span> <span data-ttu-id="69c70-113">Jest to niezbędne tylko w przypadku emitowania zagnieżdżone typy.</span><span class="sxs-lookup"><span data-stu-id="69c70-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69c70-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="69c70-114">Return Value</span></span>  
 <span data-ttu-id="69c70-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="69c70-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c70-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69c70-116">Requirements</span></span>  
 <span data-ttu-id="69c70-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="69c70-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c70-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69c70-118">See also</span></span>
- [<span data-ttu-id="69c70-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="69c70-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="69c70-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="69c70-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="69c70-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="69c70-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
