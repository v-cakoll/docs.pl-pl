---
title: "CreateALink — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateALink
api_location: alink.dll
api_type: DLLExport
f1_keywords: CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a><span data-ttu-id="92c12-102">CreateALink — Funkcja</span><span class="sxs-lookup"><span data-stu-id="92c12-102">CreateALink Function</span></span>
<span data-ttu-id="92c12-103">Tworzy wystąpienie Assembly Linker i ustawia wskaźnik do określonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="92c12-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c12-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92c12-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92c12-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92c12-105">Parameters</span></span>  
  
|<span data-ttu-id="92c12-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="92c12-106">Parameter</span></span>|<span data-ttu-id="92c12-107">Opis</span><span class="sxs-lookup"><span data-stu-id="92c12-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="92c12-108">Nazwa fizyczna jednego z interfejsów Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="92c12-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="92c12-109">Lokalizacji zawierającej po pomyślnym ukończeniu wskaźnik do `riid` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="92c12-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92c12-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92c12-110">Requirements</span></span>  
 <span data-ttu-id="92c12-111">**Biblioteka**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="92c12-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c12-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92c12-112">See Also</span></span>  
 [<span data-ttu-id="92c12-113">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="92c12-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
