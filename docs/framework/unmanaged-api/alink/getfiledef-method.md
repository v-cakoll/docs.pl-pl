---
title: "GetFileDef — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetFileDef
api_location: alink.dll
api_type: COM
f1_keywords: GetFileDef
helpviewer_keywords: GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 473cbaba8712ee247733ba3075c0163e259cf4dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getfiledef-method"></a><span data-ttu-id="a582f-102">GetFileDef — Metoda</span><span class="sxs-lookup"><span data-stu-id="a582f-102">GetFileDef Method</span></span>
<span data-ttu-id="a582f-103">Pobiera rzeczywisty token FileDef używana w metadanych (w przeciwieństwie do tokenu przypisał ALink).</span><span class="sxs-lookup"><span data-stu-id="a582f-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a582f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a582f-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a582f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a582f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a582f-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="a582f-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="a582f-107">Token dodany plik uzyskana z metody AddFile lub AddImport.</span><span class="sxs-lookup"><span data-stu-id="a582f-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="a582f-108">Odbiera FileDef token.</span><span class="sxs-lookup"><span data-stu-id="a582f-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a582f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a582f-109">Return Value</span></span>  
 <span data-ttu-id="a582f-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a582f-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a582f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a582f-111">Requirements</span></span>  
 <span data-ttu-id="a582f-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="a582f-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a582f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a582f-113">See Also</span></span>  
 [<span data-ttu-id="a582f-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a582f-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a582f-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="a582f-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a582f-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="a582f-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
