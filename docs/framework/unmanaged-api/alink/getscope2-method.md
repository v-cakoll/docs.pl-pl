---
title: "GetScope2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e57ce8fbe0b8e60c9f6f6295e9331c571aedf92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getscope2-method"></a><span data-ttu-id="31c96-102">GetScope2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="31c96-102">GetScope2 Method</span></span>
<span data-ttu-id="31c96-103">Pobiera zakres importu.</span><span class="sxs-lookup"><span data-stu-id="31c96-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31c96-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31c96-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="31c96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31c96-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="31c96-106">Identyfikator zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="31c96-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="31c96-107">Identyfikator pliku, z którego będą importowane.</span><span class="sxs-lookup"><span data-stu-id="31c96-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="31c96-108">Liczony od zera zakres do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="31c96-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="31c96-109">Odbiera Wskaźnik do [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interfejs dla wskazanego zakresu.</span><span class="sxs-lookup"><span data-stu-id="31c96-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31c96-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="31c96-110">Return Value</span></span>  
 <span data-ttu-id="31c96-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="31c96-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31c96-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31c96-112">Requirements</span></span>  
 <span data-ttu-id="31c96-113">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="31c96-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c96-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31c96-114">See Also</span></span>  
 [<span data-ttu-id="31c96-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="31c96-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="31c96-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="31c96-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="31c96-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="31c96-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
