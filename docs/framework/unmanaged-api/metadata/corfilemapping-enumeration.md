---
title: CorFileMapping — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007393"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="eea8a-102">CorFileMapping — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eea8a-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="eea8a-103">Zawiera wartości opisujące typ mapowania plików zwracanego z wywołania metody [IMetaDataInfo:: GetFileMapping —](imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eea8a-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eea8a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="eea8a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="eea8a-105">Members</span></span>  
  
|<span data-ttu-id="eea8a-106">Członek</span><span class="sxs-lookup"><span data-stu-id="eea8a-106">Member</span></span>|<span data-ttu-id="eea8a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="eea8a-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="eea8a-108">Plik jest mapowany jako plik danych.</span><span class="sxs-lookup"><span data-stu-id="eea8a-108">The file is mapped as a data file.</span></span> <span data-ttu-id="eea8a-109">Oznacza to, że `SEC_IMAGE` flaga nie została przeniesiona do funkcji Microsoft Win32 `CreateFileMapping` .</span><span class="sxs-lookup"><span data-stu-id="eea8a-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="eea8a-110">Plik jest mapowany do wykonania przy użyciu `LoadLibrary` funkcji lub `CreateFileMapping` funkcji z `SEC_IMAGE` flagą.</span><span class="sxs-lookup"><span data-stu-id="eea8a-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eea8a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eea8a-111">Requirements</span></span>  
 <span data-ttu-id="eea8a-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eea8a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eea8a-113">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="eea8a-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eea8a-114">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eea8a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea8a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eea8a-115">See also</span></span>

- [<span data-ttu-id="eea8a-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="eea8a-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="eea8a-117">GetFileMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="eea8a-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
