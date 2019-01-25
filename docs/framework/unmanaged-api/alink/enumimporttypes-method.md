---
title: EnumImportTypes — Metoda
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e437868138d7ae31d233853ecc0f709de3ee39d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512726"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="e22f2-102">EnumImportTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="e22f2-102">EnumImportTypes Method</span></span>
<span data-ttu-id="e22f2-103">Wylicza każdy typ w każdym zakresem.</span><span class="sxs-lookup"><span data-stu-id="e22f2-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e22f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e22f2-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e22f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e22f2-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e22f2-106">Dojście dla typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="e22f2-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="e22f2-107">Maksymalna liczba typów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="e22f2-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="e22f2-108">Recieves wpisz tokenów, aby nie przekroczyć `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="e22f2-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="e22f2-109">Odbiera rzeczywista liczba wpisz `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="e22f2-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e22f2-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e22f2-110">Return Value</span></span>  
 <span data-ttu-id="e22f2-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e22f2-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e22f2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e22f2-112">Requirements</span></span>  
 <span data-ttu-id="e22f2-113">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="e22f2-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22f2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e22f2-114">See also</span></span>
- [<span data-ttu-id="e22f2-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="e22f2-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e22f2-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e22f2-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e22f2-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="e22f2-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
