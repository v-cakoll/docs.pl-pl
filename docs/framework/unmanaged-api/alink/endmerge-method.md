---
title: EndMerge — Metoda
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88f594117fffedb6acafef26a9e834dd951ea5bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787526"
---
# <a name="endmerge-method"></a><span data-ttu-id="8b1c9-102">EndMerge — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b1c9-102">EndMerge Method</span></span>
<span data-ttu-id="8b1c9-103">Wskazuje, że wszystkie atrybuty niestandardowe zostały scalone z zakresem emisji.</span><span class="sxs-lookup"><span data-stu-id="8b1c9-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b1c9-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b1c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b1c9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8b1c9-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="8b1c9-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b1c9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b1c9-107">Return Value</span></span>  
 <span data-ttu-id="8b1c9-108">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8b1c9-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b1c9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b1c9-109">Requirements</span></span>  
 <span data-ttu-id="8b1c9-110">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="8b1c9-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b1c9-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b1c9-111">See also</span></span>

- [<span data-ttu-id="8b1c9-112">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b1c9-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8b1c9-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b1c9-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8b1c9-114">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="8b1c9-114">ALink API</span></span>](index.md)
