---
title: "GetALinkMessageDll — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetALinkMessageDll
api_location: alink.dll
api_type: DLLExport
f1_keywords: GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e87fe5b49a7d939a350d5d0bcb31f79eaaf333c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="95985-102">GetALinkMessageDll — Funkcja</span><span class="sxs-lookup"><span data-stu-id="95985-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="95985-103">Wyszukuje i ładuje Biblioteka DLL komunikatów.</span><span class="sxs-lookup"><span data-stu-id="95985-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="95985-104">Zwraca wartość 0, jeśli nie można znajduje się lub załadowana biblioteka DLL komunikatów.</span><span class="sxs-lookup"><span data-stu-id="95985-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="95985-105">Biblioteka DLL komunikatów, należy w podkatalogu, którego nazwa jest identyfikator języka lub w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="95985-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95985-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="95985-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="95985-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95985-107">Requirements</span></span>  
 <span data-ttu-id="95985-108">**Nagłówek:** alink.h</span><span class="sxs-lookup"><span data-stu-id="95985-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="95985-109">**Biblioteka**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="95985-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95985-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95985-110">See Also</span></span>  
 [<span data-ttu-id="95985-111">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="95985-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
