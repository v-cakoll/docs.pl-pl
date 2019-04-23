---
title: GetAssemblyRefHash — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fa8d42f9e849db6a02f6c62b37e04cf5dee016e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119655"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="41a9b-102">GetAssemblyRefHash — Metoda</span><span class="sxs-lookup"><span data-stu-id="41a9b-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="41a9b-103">Pobiera obiekt blob wyznaczania wartości skrótu dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="41a9b-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41a9b-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="41a9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41a9b-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="41a9b-106">Identyfikator zestawu, do którego będzie odnosił się wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="41a9b-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="41a9b-107">Odbiera wynikowy obiekt blob wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="41a9b-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="41a9b-108">Odbiera rozmiar w bajtach, obiektu blob wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="41a9b-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41a9b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="41a9b-109">Return Value</span></span>  
 <span data-ttu-id="41a9b-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41a9b-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41a9b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41a9b-111">Requirements</span></span>  
 <span data-ttu-id="41a9b-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="41a9b-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a9b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41a9b-113">See also</span></span>

- [<span data-ttu-id="41a9b-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="41a9b-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="41a9b-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="41a9b-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="41a9b-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="41a9b-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
