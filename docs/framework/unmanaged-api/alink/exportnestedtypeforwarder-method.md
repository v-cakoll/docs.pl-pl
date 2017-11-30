---
title: "ExportNestedTypeForwarder — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportNestedTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedTypeForwarder
helpviewer_keywords: ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 41c0984e4439b89ddee2b55bbca7a098075d6bd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="2c945-102">ExportNestedTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="2c945-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="2c945-103">Dodaje typ usługi przesyłania dalej dla typu zagnieżdżonego typu tabeli danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2c945-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c945-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c945-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="2c945-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c945-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2c945-106">Identyfikator zestawu eksportu.</span><span class="sxs-lookup"><span data-stu-id="2c945-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2c945-107">Identyfikator tokenu lub zestawu pliku, który definiuje typ pliku.</span><span class="sxs-lookup"><span data-stu-id="2c945-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="2c945-108">Token dla typu.</span><span class="sxs-lookup"><span data-stu-id="2c945-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="2c945-109">Token typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2c945-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="2c945-110">Pełni kwalifikowana nazwa typu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="2c945-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2c945-111">`ComType`flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="2c945-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="2c945-112">Odbiera token typu eksportu.</span><span class="sxs-lookup"><span data-stu-id="2c945-112">Receives token of export type.</span></span> <span data-ttu-id="2c945-113">Jest to konieczne tylko w przypadku emitowanie zagnieżdżone typy.</span><span class="sxs-lookup"><span data-stu-id="2c945-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c945-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2c945-114">Return Value</span></span>  
 <span data-ttu-id="2c945-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="2c945-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c945-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c945-116">Requirements</span></span>  
 <span data-ttu-id="2c945-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="2c945-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c945-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c945-118">See Also</span></span>  
 [<span data-ttu-id="2c945-119">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="2c945-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2c945-120">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="2c945-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2c945-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="2c945-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
