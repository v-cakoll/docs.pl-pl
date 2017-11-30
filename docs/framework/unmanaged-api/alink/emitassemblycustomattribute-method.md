---
title: "EmitAssemblyCustomAttribute — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssemblyCustomAttribute
helpviewer_keywords: EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb21ee1396a9dd0426b9b91711c2345ef66c09f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="92781-102">EmitAssemblyCustomAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="92781-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="92781-103">Wywołanie ustawiania poziomu zestawu atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="92781-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92781-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92781-104">Syntax</span></span>  
  
```  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92781-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92781-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="92781-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="92781-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="92781-107">Plik, który defiles atrybutu.</span><span class="sxs-lookup"><span data-stu-id="92781-107">File that defiles the attribute.</span></span> <span data-ttu-id="92781-108">Może mieć wartość NULL, jeśli `AssemblyID` nie wskazuje niezwiązanego modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="92781-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="92781-109">Typ atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="92781-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="92781-110">Dane niestandardowe wartości.</span><span class="sxs-lookup"><span data-stu-id="92781-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="92781-111">Długość danych wartości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="92781-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="92781-112">Wartość TRUE, jeśli atrybut niestandardowy jest powiązany z podpisywanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="92781-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="92781-113">Wartość TRUE, jeśli mają być emitowane wiele atrybutów.</span><span class="sxs-lookup"><span data-stu-id="92781-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92781-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="92781-114">Return Value</span></span>  
 <span data-ttu-id="92781-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="92781-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92781-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92781-116">Requirements</span></span>  
 <span data-ttu-id="92781-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="92781-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92781-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92781-118">See Also</span></span>  
 [<span data-ttu-id="92781-119">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="92781-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="92781-120">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="92781-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="92781-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="92781-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
