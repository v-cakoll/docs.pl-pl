---
title: "InitDbgTransportManager — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: InitDbgTransportManager
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37b849ed482f76692a63c70cbb0a3b9e1bacc8ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="671a8-102">InitDbgTransportManager — Funkcja</span><span class="sxs-lookup"><span data-stu-id="671a8-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="671a8-103">Inicjuje menedżera transportu do nawiązania połączenia zdalnego celu wyliczenie procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="671a8-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="671a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="671a8-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="671a8-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="671a8-105">Return Value</span></span>  
 <span data-ttu-id="671a8-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="671a8-106">S_OK</span></span>  
 <span data-ttu-id="671a8-107">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="671a8-107">Success.</span></span>  
  
 <span data-ttu-id="671a8-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="671a8-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="671a8-109">Funkcja nie może przydzielić pamięci dla menedżera transportu.</span><span class="sxs-lookup"><span data-stu-id="671a8-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="671a8-110">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="671a8-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="671a8-111">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="671a8-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="671a8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="671a8-112">Requirements</span></span>  
 <span data-ttu-id="671a8-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="671a8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="671a8-114">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="671a8-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="671a8-115">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="671a8-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="671a8-116">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="671a8-116">**.NET Framework Versions:** 3.5 SP1</span></span>
