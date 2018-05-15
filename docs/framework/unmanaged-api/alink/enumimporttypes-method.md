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
ms.openlocfilehash: 90319886dfe149a3d2d76451c1a8526299cf5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="23e2e-102">EnumImportTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="23e2e-102">EnumImportTypes Method</span></span>
<span data-ttu-id="23e2e-103">Wylicza każdego typu w każdym zakresem.</span><span class="sxs-lookup"><span data-stu-id="23e2e-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23e2e-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23e2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23e2e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="23e2e-106">Uchwyt dla typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="23e2e-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="23e2e-107">Maksymalna liczba typów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="23e2e-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="23e2e-108">Recieves wpisz tokenów, aby nie przekroczyć `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="23e2e-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="23e2e-109">Odbiera rzeczywistą liczbę typu w `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="23e2e-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23e2e-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="23e2e-110">Return Value</span></span>  
 <span data-ttu-id="23e2e-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="23e2e-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23e2e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23e2e-112">Requirements</span></span>  
 <span data-ttu-id="23e2e-113">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="23e2e-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e2e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23e2e-114">See Also</span></span>  
 [<span data-ttu-id="23e2e-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="23e2e-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="23e2e-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="23e2e-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="23e2e-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="23e2e-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
