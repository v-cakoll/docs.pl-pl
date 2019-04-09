---
title: CorNativeLinkType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66d650adb39a9c7dade0936ec671ae5a8b4aeecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170076"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="7a292-102">CorNativeLinkType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7a292-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="7a292-103">Zawiera wartości wskazujące typ połączone w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="7a292-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a292-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a292-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="7a292-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7a292-105">Members</span></span>  
  
|<span data-ttu-id="7a292-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7a292-106">Member</span></span>|<span data-ttu-id="7a292-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7a292-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="7a292-108">Wskazuje brak słów kluczowych określony.</span><span class="sxs-lookup"><span data-stu-id="7a292-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="7a292-109">Wskazuje, że zostanie określone słowo kluczowe ANSI.</span><span class="sxs-lookup"><span data-stu-id="7a292-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="7a292-110">Wskazuje, że określono Unicode — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="7a292-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="7a292-111">Wskazuje, że określono auto — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="7a292-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="7a292-112">Wskazuje, że zostanie określone słowo kluczowe OLE.</span><span class="sxs-lookup"><span data-stu-id="7a292-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="7a292-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="7a292-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a292-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a292-114">Requirements</span></span>  
 <span data-ttu-id="7a292-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a292-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a292-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7a292-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a292-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a292-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7a292-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7a292-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a292-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a292-119">See also</span></span>

- [<span data-ttu-id="7a292-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="7a292-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
