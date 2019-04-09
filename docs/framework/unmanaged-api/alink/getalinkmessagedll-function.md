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
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163023"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="8699c-102">GetALinkMessageDll — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8699c-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="8699c-103">Umożliwia znalezienie i ładuje Biblioteka DLL komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8699c-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="8699c-104">Zwraca wartość 0, jeśli biblioteka DLL komunikatu nie można się lub załadowane.</span><span class="sxs-lookup"><span data-stu-id="8699c-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="8699c-105">Biblioteka DLL komunikatu powinna być w podkatalogu, której nazwa to identyfikator języka lub w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8699c-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8699c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8699c-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="8699c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8699c-107">Requirements</span></span>  
 <span data-ttu-id="8699c-108">**Nagłówek:** alink.h</span><span class="sxs-lookup"><span data-stu-id="8699c-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="8699c-109">**Biblioteka**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="8699c-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8699c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8699c-110">See also</span></span>

- [<span data-ttu-id="8699c-111">Al.exe (Konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="8699c-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
