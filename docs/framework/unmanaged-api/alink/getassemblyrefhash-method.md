---
title: "GetAssemblyRefHash — Metoda"
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
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99ae38025f223d669a428738783676ebc0687554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="73470-102">GetAssemblyRefHash — Metoda</span><span class="sxs-lookup"><span data-stu-id="73470-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="73470-103">Pobiera obiekt blob wyznaczania wartości skrótu dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="73470-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73470-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73470-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73470-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73470-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="73470-106">Identyfikator zestawu, do którego będzie można znaleźć skrót.</span><span class="sxs-lookup"><span data-stu-id="73470-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="73470-107">Odbiera wynikowego obiektu blob generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="73470-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="73470-108">Odbiera rozmiar w bajtach obiektu blob generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="73470-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73470-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73470-109">Return Value</span></span>  
 <span data-ttu-id="73470-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="73470-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73470-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73470-111">Requirements</span></span>  
 <span data-ttu-id="73470-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="73470-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73470-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73470-113">See Also</span></span>  
 [<span data-ttu-id="73470-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="73470-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="73470-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="73470-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="73470-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="73470-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
