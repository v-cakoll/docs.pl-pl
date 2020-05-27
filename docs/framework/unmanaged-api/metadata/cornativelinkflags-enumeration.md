---
title: CorNativeLinkFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: 9211af4726617598f3dd8772383cade6368e6c08
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007627"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="e1e5b-102">CorNativeLinkFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e1e5b-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="e1e5b-103">Dostarcza wartości flag używanych przez konsolidatora podczas łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="e1e5b-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1e5b-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e1e5b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e1e5b-105">Members</span></span>  
  
|<span data-ttu-id="e1e5b-106">Członek</span><span class="sxs-lookup"><span data-stu-id="e1e5b-106">Member</span></span>|<span data-ttu-id="e1e5b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e1e5b-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="e1e5b-108">Oznacza brak flag.</span><span class="sxs-lookup"><span data-stu-id="e1e5b-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="e1e5b-109">Wskazuje `setLastError` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e1e5b-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="e1e5b-110">Wskazuje `nomangle` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e1e5b-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="e1e5b-111">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="e1e5b-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1e5b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1e5b-112">Requirements</span></span>  
 <span data-ttu-id="e1e5b-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1e5b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1e5b-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e1e5b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1e5b-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e1e5b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1e5b-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1e5b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e5b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1e5b-117">See also</span></span>

- [<span data-ttu-id="e1e5b-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="e1e5b-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
