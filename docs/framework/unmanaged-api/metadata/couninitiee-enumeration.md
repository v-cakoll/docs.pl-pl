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
ms.openlocfilehash: e5cbd8c5b1bb048088fe137b1359d0bb9e29af20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176126"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="7c44d-102">COUNINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7c44d-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="7c44d-103">Określa stałe używane przez [CoUninitializeEEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) podczas inicjowania środowiska wykonawczego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="7c44d-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c44d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c44d-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="7c44d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7c44d-105">Members</span></span>  
  
|<span data-ttu-id="7c44d-106">Członek</span><span class="sxs-lookup"><span data-stu-id="7c44d-106">Member</span></span>|<span data-ttu-id="7c44d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7c44d-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="7c44d-108">Wskazuje domyślny tryb niezainicjowania.</span><span class="sxs-lookup"><span data-stu-id="7c44d-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="7c44d-109">Wskazuje tryb niezainicjowania dla zwalniania złożenia.</span><span class="sxs-lookup"><span data-stu-id="7c44d-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c44d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c44d-110">Requirements</span></span>  
 <span data-ttu-id="7c44d-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c44d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c44d-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="7c44d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c44d-113">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c44d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c44d-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c44d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c44d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c44d-115">See also</span></span>

- [<span data-ttu-id="7c44d-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="7c44d-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
