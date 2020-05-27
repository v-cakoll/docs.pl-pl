---
title: COUNINITIEE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: 14942680a79c4d1fcc69092a4f752738db1fb0b0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008922"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="f6083-102">COUNINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f6083-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="f6083-103">Określa stałe używane przez [CoUninitializeEE —](../hosting/couninitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f6083-103">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6083-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6083-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="f6083-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f6083-105">Members</span></span>  
  
|<span data-ttu-id="f6083-106">Członek</span><span class="sxs-lookup"><span data-stu-id="f6083-106">Member</span></span>|<span data-ttu-id="f6083-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f6083-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="f6083-108">Wskazuje domyślny tryb uninicjującym.</span><span class="sxs-lookup"><span data-stu-id="f6083-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="f6083-109">Wskazuje tryb odinicjowania w przypadku zwalniania zestawu.</span><span class="sxs-lookup"><span data-stu-id="f6083-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6083-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6083-110">Requirements</span></span>  
 <span data-ttu-id="f6083-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6083-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6083-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f6083-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6083-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f6083-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6083-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6083-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6083-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6083-115">See also</span></span>

- [<span data-ttu-id="f6083-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="f6083-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
