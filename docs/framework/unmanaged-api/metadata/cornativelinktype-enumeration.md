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
ms.openlocfilehash: 944c641c39ddef7add0e9f382dc7d35068668455
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781719"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="54020-102">CorNativeLinkType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="54020-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="54020-103">Zawiera wartości wskazujące typ połączone w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="54020-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54020-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54020-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="54020-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="54020-105">Members</span></span>  
  
|<span data-ttu-id="54020-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="54020-106">Member</span></span>|<span data-ttu-id="54020-107">Opis</span><span class="sxs-lookup"><span data-stu-id="54020-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="54020-108">Wskazuje brak słów kluczowych określony.</span><span class="sxs-lookup"><span data-stu-id="54020-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="54020-109">Wskazuje, że zostanie określone słowo kluczowe ANSI.</span><span class="sxs-lookup"><span data-stu-id="54020-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="54020-110">Wskazuje, że określono Unicode — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="54020-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="54020-111">Wskazuje, że określono auto — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="54020-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="54020-112">Wskazuje, że zostanie określone słowo kluczowe OLE.</span><span class="sxs-lookup"><span data-stu-id="54020-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="54020-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="54020-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54020-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54020-114">Requirements</span></span>  
 <span data-ttu-id="54020-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54020-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54020-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="54020-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54020-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54020-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54020-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54020-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54020-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54020-119">See also</span></span>

- [<span data-ttu-id="54020-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="54020-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
