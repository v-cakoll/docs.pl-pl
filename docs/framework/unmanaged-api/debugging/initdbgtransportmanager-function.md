---
title: InitDbgTransportManager — Funkcja
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: e18ceb25b9c58a9710ef967cb071e3ef55beea8c
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421049"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="ad93d-102">InitDbgTransportManager — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ad93d-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="ad93d-103">Inicjuje menedżera transportu, aby połączyć się ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ad93d-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad93d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad93d-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ad93d-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ad93d-105">Return Value</span></span>  
 <span data-ttu-id="ad93d-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad93d-106">S_OK</span></span>  
 <span data-ttu-id="ad93d-107">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="ad93d-107">Success.</span></span>  
  
 <span data-ttu-id="ad93d-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ad93d-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ad93d-109">Funkcja nie może przydzielić pamięci dla menedżera transportu.</span><span class="sxs-lookup"><span data-stu-id="ad93d-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="ad93d-110">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="ad93d-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ad93d-111">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="ad93d-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad93d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad93d-112">Requirements</span></span>  
 <span data-ttu-id="ad93d-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad93d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad93d-114">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="ad93d-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ad93d-115">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="ad93d-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ad93d-116">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="ad93d-116">**.NET Framework Versions:** 3.5 SP1</span></span>
