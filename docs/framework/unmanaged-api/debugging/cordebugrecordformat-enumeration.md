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
ms.openlocfilehash: cfbd856c73ab10642a7cf7c16cfb2d70e7fe9756
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795732"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="1530f-102">Wyliczenie CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="1530f-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="1530f-103">Opisuje format danych w tablicy bajtów, który zawiera informacje na temat natywnego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1530f-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1530f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1530f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="1530f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1530f-105">Members</span></span>  
  
|<span data-ttu-id="1530f-106">Członek</span><span class="sxs-lookup"><span data-stu-id="1530f-106">Member</span></span>|<span data-ttu-id="1530f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1530f-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="1530f-108">Dane to 32-bitowy rekord wyjątku systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1530f-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="1530f-109">Dane to 64-bitowy rekord wyjątku systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1530f-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1530f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1530f-110">Remarks</span></span>  
 <span data-ttu-id="1530f-111">Element członkowski `CorDebugRecordFormat` wyliczenia jest przesyłany do metody [DecodeEvent](icordebugprocess6-decodeevent-method.md) w celu wskazania formatu tablicy bajtów w `pRecord` argumencie.</span><span class="sxs-lookup"><span data-stu-id="1530f-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1530f-112">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1530f-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1530f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1530f-113">Requirements</span></span>  
 <span data-ttu-id="1530f-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1530f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1530f-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1530f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1530f-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1530f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1530f-117">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1530f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1530f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1530f-118">See also</span></span>

- [<span data-ttu-id="1530f-119">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1530f-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
