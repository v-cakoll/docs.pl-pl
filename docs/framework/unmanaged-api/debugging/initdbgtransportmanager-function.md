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
ms.openlocfilehash: 2d67bee3ea0e57080179b3fbb7e0b4193860c44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103288"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="8ca43-102">InitDbgTransportManager — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8ca43-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="8ca43-103">Inicjuje menedżera transportu, aby połączyć się ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8ca43-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ca43-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8ca43-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8ca43-105">Return Value</span></span>  
 <span data-ttu-id="8ca43-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ca43-106">S_OK</span></span>  
 <span data-ttu-id="8ca43-107">Prawnego.</span><span class="sxs-lookup"><span data-stu-id="8ca43-107">Success.</span></span>  
  
 <span data-ttu-id="8ca43-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8ca43-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="8ca43-109">Funkcja nie może przydzielić pamięci dla menedżera transportu.</span><span class="sxs-lookup"><span data-stu-id="8ca43-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="8ca43-110">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="8ca43-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="8ca43-111">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="8ca43-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca43-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ca43-112">Requirements</span></span>  
 <span data-ttu-id="8ca43-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca43-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca43-114">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="8ca43-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="8ca43-115">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="8ca43-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="8ca43-116">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="8ca43-116">**.NET Framework Versions:** 3.5 SP1</span></span>
