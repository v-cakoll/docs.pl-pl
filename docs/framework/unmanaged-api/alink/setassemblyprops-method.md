---
title: "SetAssemblyProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyProps
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyProps
helpviewer_keywords: SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0245b6b1e30174bb3496d3d6ab674ccc00fb9fee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="83f03-102">SetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="83f03-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="83f03-103">Przypisuje poziom zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="83f03-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83f03-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83f03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83f03-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="83f03-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f03-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="83f03-107">Plik, który definiuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="83f03-107">File that defines the property.</span></span> <span data-ttu-id="83f03-108">Może mieć wartość NULL, jeśli `AssemblyID` nie wskazuje niezwiązanego modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="83f03-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="83f03-109">Wskazuje opcję, aby zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="83f03-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="83f03-110">Nowa wartość opcji.</span><span class="sxs-lookup"><span data-stu-id="83f03-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83f03-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="83f03-111">Return Value</span></span>  
 <span data-ttu-id="83f03-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="83f03-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83f03-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83f03-113">Requirements</span></span>  
 <span data-ttu-id="83f03-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="83f03-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f03-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83f03-115">See Also</span></span>  
 [<span data-ttu-id="83f03-116">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="83f03-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="83f03-117">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="83f03-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="83f03-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="83f03-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
