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
ms.openlocfilehash: 4dfb31a2fad8a07b3821ac85bbb43b25693f11d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404109"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="1507a-102">ExportNestedTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="1507a-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="1507a-103">Dodaje typ usługi przesyłania dalej dla typu zagnieżdżonego typu tabeli danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1507a-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1507a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1507a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1507a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1507a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1507a-106">Identyfikator zestawu eksportu.</span><span class="sxs-lookup"><span data-stu-id="1507a-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1507a-107">Identyfikator tokenu lub zestawu pliku, który definiuje typ pliku.</span><span class="sxs-lookup"><span data-stu-id="1507a-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="1507a-108">Token dla typu.</span><span class="sxs-lookup"><span data-stu-id="1507a-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="1507a-109">Token typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1507a-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="1507a-110">Pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="1507a-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1507a-111">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="1507a-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="1507a-112">Odbiera token typu eksportu.</span><span class="sxs-lookup"><span data-stu-id="1507a-112">Receives token of export type.</span></span> <span data-ttu-id="1507a-113">Jest to konieczne tylko w przypadku emitowanie zagnieżdżone typy.</span><span class="sxs-lookup"><span data-stu-id="1507a-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1507a-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1507a-114">Return Value</span></span>  
 <span data-ttu-id="1507a-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1507a-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1507a-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1507a-116">Requirements</span></span>  
 <span data-ttu-id="1507a-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="1507a-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1507a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1507a-118">See Also</span></span>  
 [<span data-ttu-id="1507a-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="1507a-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1507a-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1507a-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1507a-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="1507a-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
