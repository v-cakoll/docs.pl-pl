---
title: ECustomDumpFlavor — Wyliczenie
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 9b4c1187945b4c243375a3096c3a8a3b22599aef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616284"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="14ac6-102">ECustomDumpFlavor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="14ac6-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="14ac6-103">Zawiera wartości wskazujące, które elementy mają być uwzględnione w niestandardowym podzestawie zrzutu sterty podczas raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="14ac6-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14ac6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14ac6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="14ac6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="14ac6-105">Members</span></span>  
  
|<span data-ttu-id="14ac6-106">Członek</span><span class="sxs-lookup"><span data-stu-id="14ac6-106">Member</span></span>|<span data-ttu-id="14ac6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="14ac6-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="14ac6-108">Określa, że niestandardowy zrzut sterty powinien rozpoczynać się jako minizrzutu i dołączać dodatkowe dane określone przez wystąpienia [CustomDumpItem —](customdumpitem-structure.md) przesłane do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="14ac6-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="14ac6-109">Określa, że zrzut sterty niestandardowej ma zbierać wszystkie dane stanu czasu wykonywania, które nie były przydzielane dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="14ac6-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14ac6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14ac6-110">Remarks</span></span>  
 <span data-ttu-id="14ac6-111">Parametr typu `ECustomDumpFlavor` jest przesyłany do metody [ICLRErrorReportingManager:: BeginCustomDump —](iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="14ac6-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14ac6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14ac6-112">Requirements</span></span>  
 <span data-ttu-id="14ac6-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14ac6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14ac6-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="14ac6-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14ac6-115">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="14ac6-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14ac6-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14ac6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ac6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14ac6-117">See also</span></span>

- [<span data-ttu-id="14ac6-118">ECustomDumpItemKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="14ac6-118">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="14ac6-119">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="14ac6-119">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="14ac6-120">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="14ac6-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
