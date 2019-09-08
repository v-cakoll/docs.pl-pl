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
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787620"
---
# <a name="createalink-function"></a><span data-ttu-id="db297-102">CreateALink — Funkcja</span><span class="sxs-lookup"><span data-stu-id="db297-102">CreateALink Function</span></span>
<span data-ttu-id="db297-103">Tworzy wystąpienie konsolidatora zestawu i ustawia wskaźnik do określonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db297-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db297-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db297-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db297-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db297-105">Parameters</span></span>  
  
|<span data-ttu-id="db297-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="db297-106">Parameter</span></span>|<span data-ttu-id="db297-107">Opis</span><span class="sxs-lookup"><span data-stu-id="db297-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="db297-108">Nazwa fizyczna jednego z interfejsów konsolidatora zestawu.</span><span class="sxs-lookup"><span data-stu-id="db297-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="db297-109">Lokalizacja po pomyślnym zakończeniu zawiera wskaźnik do `riid` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db297-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db297-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db297-110">Requirements</span></span>  
 <span data-ttu-id="db297-111">**Biblioteka**: Alink. dll</span><span class="sxs-lookup"><span data-stu-id="db297-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db297-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db297-112">See also</span></span>

- [<span data-ttu-id="db297-113">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="db297-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
