---
title: COINITIEE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48f15cc08167baaadc61787b8b1f7167304f0cae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569482"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="4ebc3-102">COINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4ebc3-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="4ebc3-103">Określa stałe używane przez [coinitializeee —](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="4ebc3-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ebc3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ebc3-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="4ebc3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4ebc3-105">Members</span></span>  
  
|<span data-ttu-id="4ebc3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4ebc3-106">Member</span></span>|<span data-ttu-id="4ebc3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4ebc3-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="4ebc3-108">Domyślny tryb inicjowania.</span><span class="sxs-lookup"><span data-stu-id="4ebc3-108">Default initialization mode.</span></span> <span data-ttu-id="4ebc3-109">To inicjuje środowisko uruchomieniowe i tworzy domyślną <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="4ebc3-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="4ebc3-110">Inicjuje, aby uruchomić zarządzanej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="4ebc3-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="4ebc3-111">Inicjuje do uruchamiania zarządzanego EXE.</span><span class="sxs-lookup"><span data-stu-id="4ebc3-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="4ebc3-112">To inicjuje środowiska uruchomieniowego, ale nie tworzy domyślnie <xref:System.AppDomain>, który jest tworzony po wprowadzeniu główne procedury pliku exe.</span><span class="sxs-lookup"><span data-stu-id="4ebc3-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ebc3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ebc3-113">Requirements</span></span>  
 <span data-ttu-id="4ebc3-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ebc3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ebc3-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4ebc3-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ebc3-116">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ebc3-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ebc3-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ebc3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebc3-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ebc3-118">See also</span></span>
- [<span data-ttu-id="4ebc3-119">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="4ebc3-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
