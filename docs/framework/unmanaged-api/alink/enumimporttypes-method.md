---
title: "EnumImportTypes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: EnumImportTypes
helpviewer_keywords: EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08644816d3fa11ade5a8ebee1573e8f66d526101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="751d5-102">EnumImportTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="751d5-102">EnumImportTypes Method</span></span>
<span data-ttu-id="751d5-103">Wylicza każdego typu w każdym zakresem.</span><span class="sxs-lookup"><span data-stu-id="751d5-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="751d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="751d5-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="751d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="751d5-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="751d5-106">Uchwyt dla typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="751d5-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="751d5-107">Maksymalna liczba typów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="751d5-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="751d5-108">Recieves wpisz tokenów, aby nie przekroczyć `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="751d5-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="751d5-109">Odbiera rzeczywistą liczbę typu w `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="751d5-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="751d5-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="751d5-110">Return Value</span></span>  
 <span data-ttu-id="751d5-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="751d5-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="751d5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="751d5-112">Requirements</span></span>  
 <span data-ttu-id="751d5-113">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="751d5-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="751d5-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="751d5-114">See Also</span></span>  
 [<span data-ttu-id="751d5-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="751d5-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="751d5-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="751d5-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="751d5-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="751d5-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
