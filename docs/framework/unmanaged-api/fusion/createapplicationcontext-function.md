---
title: CreateApplicationContext — Funkcja
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25364330dafdf858c4b41e9a05731c37e97fbb57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795431"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="5b802-102">CreateApplicationContext — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5b802-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="5b802-103">Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5b802-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b802-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b802-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b802-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b802-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="5b802-106">podczas Wskaźnik do przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5b802-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="5b802-107">określoną Wskaźnik do kontekstu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5b802-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b802-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b802-108">Requirements</span></span>  
 <span data-ttu-id="5b802-109">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b802-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b802-110">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5b802-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5b802-111">**Biblioteki** Uwzględnione jako zasób w bibliotece Fusion. dll</span><span class="sxs-lookup"><span data-stu-id="5b802-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="5b802-112">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b802-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b802-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b802-113">See also</span></span>

- [<span data-ttu-id="5b802-114">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="5b802-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="5b802-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="5b802-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="5b802-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="5b802-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
