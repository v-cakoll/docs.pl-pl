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
ms.openlocfilehash: e188fe80e770481aac02244a2c105639e4da19e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108892"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="138ce-102">CreateApplicationContext — Funkcja</span><span class="sxs-lookup"><span data-stu-id="138ce-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="138ce-103">Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="138ce-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="138ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="138ce-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="138ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="138ce-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="138ce-106">podczas Wskaźnik do przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="138ce-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="138ce-107">określoną Wskaźnik do kontekstu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="138ce-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="138ce-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="138ce-108">Requirements</span></span>  
 <span data-ttu-id="138ce-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="138ce-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="138ce-110">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="138ce-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="138ce-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece Fusion. dll</span><span class="sxs-lookup"><span data-stu-id="138ce-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="138ce-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="138ce-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="138ce-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="138ce-113">See also</span></span>

- [<span data-ttu-id="138ce-114">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="138ce-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="138ce-115">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="138ce-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="138ce-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="138ce-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
