---
title: GetALinkMessageDll — Funkcja
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 395dc85ad638e8a790962a4aa38019612c360ce1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="e4a22-102">GetALinkMessageDll — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e4a22-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="e4a22-103">Wyszukuje i ładuje Biblioteka DLL komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e4a22-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="e4a22-104">Zwraca wartość 0, jeśli nie można znajduje się lub załadowana biblioteka DLL komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e4a22-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="e4a22-105">Biblioteka DLL komunikatów, należy w podkatalogu, którego nazwa jest identyfikator języka lub w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e4a22-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a22-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4a22-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="e4a22-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4a22-107">Requirements</span></span>  
 <span data-ttu-id="e4a22-108">**Nagłówek:** alink.h</span><span class="sxs-lookup"><span data-stu-id="e4a22-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="e4a22-109">**Biblioteka**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="e4a22-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a22-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4a22-110">See Also</span></span>  
 [<span data-ttu-id="e4a22-111">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="e4a22-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
