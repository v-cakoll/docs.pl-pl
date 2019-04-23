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
ms.openlocfilehash: 050ed0bbd4da38bede5a56ff95d0243f5f3cf1da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220087"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="ac6ba-102">ExportNestedTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac6ba-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="ac6ba-103">Dodaje typ usługi przesyłania dalej dla typu zagnieżdżonego do tabeli typu danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac6ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac6ba-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ac6ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac6ba-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ac6ba-106">Identyfikator zestawu, aby wyeksportować z.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ac6ba-107">Identyfikator tokenu lub zestawu w pliku, który definiuje typ pliku.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="ac6ba-108">Token dla typu.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="ac6ba-109">Token typie elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="ac6ba-110">W pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ac6ba-111">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="ac6ba-112">Odbiera token typu eksportu.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-112">Receives token of export type.</span></span> <span data-ttu-id="ac6ba-113">Jest to niezbędne tylko w przypadku emitowania zagnieżdżone typy.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac6ba-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ac6ba-114">Return Value</span></span>  
 <span data-ttu-id="ac6ba-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ac6ba-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac6ba-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac6ba-116">Requirements</span></span>  
 <span data-ttu-id="ac6ba-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="ac6ba-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac6ba-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac6ba-118">See also</span></span>

- [<span data-ttu-id="ac6ba-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac6ba-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ac6ba-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac6ba-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ac6ba-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="ac6ba-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
