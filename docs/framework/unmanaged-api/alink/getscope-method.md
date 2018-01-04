---
title: GetScope metoda1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetScope
api_location: alink.dll
api_type: COM
f1_keywords: GetScope
helpviewer_keywords: GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cb51efc3f431dac4a10cc7582e2b43500ccba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getscope-method1"></a><span data-ttu-id="27f65-102">GetScope metoda1</span><span class="sxs-lookup"><span data-stu-id="27f65-102">GetScope Method1</span></span>
<span data-ttu-id="27f65-103">Pobiera zakres importu.</span><span class="sxs-lookup"><span data-stu-id="27f65-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f65-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27f65-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27f65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27f65-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="27f65-106">Unikatowy identyfikator zestawu, aby zaimportować.</span><span class="sxs-lookup"><span data-stu-id="27f65-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="27f65-107">Unikatowy identyfikator pliku importowanego.</span><span class="sxs-lookup"><span data-stu-id="27f65-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="27f65-108">Liczony od zera zakres do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="27f65-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="27f65-109">Odbiera [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="27f65-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27f65-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="27f65-110">Return Value</span></span>  
 <span data-ttu-id="27f65-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="27f65-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f65-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27f65-112">Requirements</span></span>  
 <span data-ttu-id="27f65-113">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="27f65-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f65-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27f65-114">See Also</span></span>  
 [<span data-ttu-id="27f65-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="27f65-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="27f65-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="27f65-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="27f65-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="27f65-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
