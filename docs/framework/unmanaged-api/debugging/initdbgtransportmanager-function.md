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
ms.openlocfilehash: 74cb2c7d1f79d23e1331cc7192ba2d6acfd9835c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="df3c3-102">InitDbgTransportManager — Funkcja</span><span class="sxs-lookup"><span data-stu-id="df3c3-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="df3c3-103">Inicjuje menedżera transportu do nawiązania połączenia zdalnego celu wyliczenie procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="df3c3-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df3c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df3c3-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="df3c3-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="df3c3-105">Return Value</span></span>  
 <span data-ttu-id="df3c3-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="df3c3-106">S_OK</span></span>  
 <span data-ttu-id="df3c3-107">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="df3c3-107">Success.</span></span>  
  
 <span data-ttu-id="df3c3-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="df3c3-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="df3c3-109">Funkcja nie może przydzielić pamięci dla menedżera transportu.</span><span class="sxs-lookup"><span data-stu-id="df3c3-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="df3c3-110">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="df3c3-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="df3c3-111">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="df3c3-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df3c3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df3c3-112">Requirements</span></span>  
 <span data-ttu-id="df3c3-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df3c3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df3c3-114">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="df3c3-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="df3c3-115">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="df3c3-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="df3c3-116">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="df3c3-116">**.NET Framework Versions:** 3.5 SP1</span></span>
