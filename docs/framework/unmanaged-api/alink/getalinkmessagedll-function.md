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
ms.openlocfilehash: 632f19e0ead57d5508265fece578bb22f18ba54a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722728"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="f39ec-102">GetALinkMessageDll — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f39ec-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="f39ec-103">Umożliwia znalezienie i ładuje Biblioteka DLL komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f39ec-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="f39ec-104">Zwraca wartość 0, jeśli biblioteka DLL komunikatu nie można się lub załadowane.</span><span class="sxs-lookup"><span data-stu-id="f39ec-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="f39ec-105">Biblioteka DLL komunikatu powinna być w podkatalogu, której nazwa to identyfikator języka lub w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f39ec-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39ec-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f39ec-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f39ec-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f39ec-107">Requirements</span></span>  
 <span data-ttu-id="f39ec-108">**Nagłówek:** alink.h</span><span class="sxs-lookup"><span data-stu-id="f39ec-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="f39ec-109">**Biblioteka**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="f39ec-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39ec-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f39ec-110">See also</span></span>
- [<span data-ttu-id="f39ec-111">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="f39ec-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
