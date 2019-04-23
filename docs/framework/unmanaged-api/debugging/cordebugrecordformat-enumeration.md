---
title: Wyliczenie CorDebugRecordFormat
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: add1458bb3a50a5e5433e8cc7baaf47d750c927d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083676"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="54982-102">Wyliczenie CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="54982-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="54982-103">W tym artykule opisano format danych w tablicy bajtowej, zawierający informacje o zdarzeniu debugowania natywnych wyjątku.</span><span class="sxs-lookup"><span data-stu-id="54982-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54982-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54982-104">Syntax</span></span>  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="54982-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="54982-105">Members</span></span>  
  
|<span data-ttu-id="54982-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="54982-106">Member</span></span>|<span data-ttu-id="54982-107">Opis</span><span class="sxs-lookup"><span data-stu-id="54982-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="54982-108">Dane jest rekordem wyjątku Windows 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="54982-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="54982-109">Dane jest rekordem wyjątku Windows 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="54982-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54982-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54982-110">Remarks</span></span>  
 <span data-ttu-id="54982-111">Członek `CorDebugRecordFormat` wyliczenia jest przekazywany do [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metodę w celu wskazania format tablicę bajtów w jego `pRecord` argumentu.</span><span class="sxs-lookup"><span data-stu-id="54982-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54982-112">To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="54982-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54982-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54982-113">Requirements</span></span>  
 <span data-ttu-id="54982-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54982-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54982-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54982-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54982-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54982-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54982-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54982-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54982-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54982-118">See also</span></span>

- [<span data-ttu-id="54982-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="54982-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
