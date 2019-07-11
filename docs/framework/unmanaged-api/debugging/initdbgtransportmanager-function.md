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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948e97064d12dc5b2044faf35aa374e5ba5f2592
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764785"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="09a4a-102">InitDbgTransportManager — Funkcja</span><span class="sxs-lookup"><span data-stu-id="09a4a-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="09a4a-103">Inicjuje menedżera transportu nawiązać zdalnego obiektu docelowego dla wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="09a4a-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09a4a-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="09a4a-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="09a4a-105">Return Value</span></span>  
 <span data-ttu-id="09a4a-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="09a4a-106">S_OK</span></span>  
 <span data-ttu-id="09a4a-107">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="09a4a-107">Success.</span></span>  
  
 <span data-ttu-id="09a4a-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="09a4a-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="09a4a-109">Funkcja nie może przydzielić pamięci dla menedżera transportu.</span><span class="sxs-lookup"><span data-stu-id="09a4a-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="09a4a-110">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="09a4a-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="09a4a-111">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="09a4a-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09a4a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09a4a-112">Requirements</span></span>  
 <span data-ttu-id="09a4a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09a4a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a4a-114">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="09a4a-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="09a4a-115">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="09a4a-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="09a4a-116">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="09a4a-116">**.NET Framework Versions:** 3.5 SP1</span></span>
