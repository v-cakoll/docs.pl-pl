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
ms.openlocfilehash: 2ccc038b4420040779dae70f15e3a8827ba94180
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444103"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="ddde2-102">COINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ddde2-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="ddde2-103">Określa stałe używane przez [CoInitializeEE —](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ddde2-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddde2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddde2-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="ddde2-105">Members</span><span class="sxs-lookup"><span data-stu-id="ddde2-105">Members</span></span>  
  
|<span data-ttu-id="ddde2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ddde2-106">Member</span></span>|<span data-ttu-id="ddde2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ddde2-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="ddde2-108">Domyślny tryb inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="ddde2-108">Default initialization mode.</span></span> <span data-ttu-id="ddde2-109">Spowoduje to zainicjowanie środowiska uruchomieniowego i utworzenie domyślnego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ddde2-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="ddde2-110">Inicjuje się uruchamianie zarządzanej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="ddde2-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="ddde2-111">Jest inicjowany do uruchamiania zarządzanego pliku EXE.</span><span class="sxs-lookup"><span data-stu-id="ddde2-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="ddde2-112">To inicjuje środowisko uruchomieniowe, ale nie tworzy domyślnego <xref:System.AppDomain>, które jest tworzone po wprowadzeniu głównej procedury pliku EXE.</span><span class="sxs-lookup"><span data-stu-id="ddde2-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ddde2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddde2-113">Requirements</span></span>  
 <span data-ttu-id="ddde2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddde2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddde2-115">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ddde2-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddde2-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ddde2-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ddde2-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddde2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddde2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddde2-118">See also</span></span>

- [<span data-ttu-id="ddde2-119">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="ddde2-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
