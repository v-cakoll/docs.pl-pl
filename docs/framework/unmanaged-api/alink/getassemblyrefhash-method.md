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
ms.openlocfilehash: d19eebaa3aa0ebb6f9807f0cf277b7ed6183c148
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777192"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="970f7-102">GetAssemblyRefHash — Metoda</span><span class="sxs-lookup"><span data-stu-id="970f7-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="970f7-103">Pobiera obiekt BLOB mieszania dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="970f7-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="970f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="970f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="970f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="970f7-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="970f7-106">Identyfikator zestawu, do którego odwołuje się skrót.</span><span class="sxs-lookup"><span data-stu-id="970f7-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="970f7-107">Odbiera wynikowy obiekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="970f7-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="970f7-108">Odbiera rozmiar, w bajtach, obiektu BLOB mieszania.</span><span class="sxs-lookup"><span data-stu-id="970f7-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="970f7-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="970f7-109">Return Value</span></span>  
 <span data-ttu-id="970f7-110">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="970f7-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="970f7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="970f7-111">Requirements</span></span>  
 <span data-ttu-id="970f7-112">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="970f7-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="970f7-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="970f7-113">See also</span></span>

- [<span data-ttu-id="970f7-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="970f7-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="970f7-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="970f7-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="970f7-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="970f7-116">ALink API</span></span>](index.md)
