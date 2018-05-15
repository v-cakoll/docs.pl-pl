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
ms.openlocfilehash: ccf60d067af356dda1870a2fb1dcca21966f16a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="d7541-102">GetAssemblyRefHash — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7541-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="d7541-103">Pobiera obiekt blob wyznaczania wartości skrótu dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d7541-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7541-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7541-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7541-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7541-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="d7541-106">Identyfikator zestawu, do którego będzie można znaleźć skrót.</span><span class="sxs-lookup"><span data-stu-id="d7541-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="d7541-107">Odbiera wynikowego obiektu blob generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="d7541-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="d7541-108">Odbiera rozmiar w bajtach obiektu blob generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="d7541-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7541-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d7541-109">Return Value</span></span>  
 <span data-ttu-id="d7541-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d7541-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7541-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7541-111">Requirements</span></span>  
 <span data-ttu-id="d7541-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="d7541-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7541-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7541-113">See Also</span></span>  
 [<span data-ttu-id="d7541-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7541-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d7541-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7541-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d7541-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="d7541-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
