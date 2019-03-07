---
title: CreateALink — Funkcja
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11117db08d58684cc854400424d1836ec35b8c12
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498015"
---
# <a name="createalink-function"></a><span data-ttu-id="af1f8-102">CreateALink — Funkcja</span><span class="sxs-lookup"><span data-stu-id="af1f8-102">CreateALink Function</span></span>
<span data-ttu-id="af1f8-103">Tworzy wystąpienie programu Assembly Linker i ustawia wskaźnik do określonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="af1f8-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af1f8-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af1f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af1f8-105">Parameters</span></span>  
  
|<span data-ttu-id="af1f8-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="af1f8-106">Parameter</span></span>|<span data-ttu-id="af1f8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="af1f8-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="af1f8-108">Nazwa fizyczna jednego z interfejsów Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="af1f8-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="af1f8-109">Lokalizację zawierającą od pomyślnego zakończenia wskaźnika do `riid` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="af1f8-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af1f8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af1f8-110">Requirements</span></span>  
 <span data-ttu-id="af1f8-111">**Biblioteka**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="af1f8-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1f8-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af1f8-112">See also</span></span>
- [<span data-ttu-id="af1f8-113">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="af1f8-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
