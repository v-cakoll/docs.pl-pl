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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 719f0522cc43625a4d6cc8afa838d869e47b40d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781833"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="1f3b1-102">CorFileMapping — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1f3b1-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="1f3b1-103">Zawiera wartości, które opisują typ mapowania pliku, który jest zwracany po wywołaniu [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1f3b1-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f3b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f3b1-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="1f3b1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1f3b1-105">Members</span></span>  
  
|<span data-ttu-id="1f3b1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1f3b1-106">Member</span></span>|<span data-ttu-id="1f3b1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1f3b1-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="1f3b1-108">Plik jest mapowany jako pliku danych.</span><span class="sxs-lookup"><span data-stu-id="1f3b1-108">The file is mapped as a data file.</span></span> <span data-ttu-id="1f3b1-109">Oznacza to, że `SEC_IMAGE` flaga nie został przekazany do Microsoft Win32 `CreateFileMapping` funkcji.</span><span class="sxs-lookup"><span data-stu-id="1f3b1-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="1f3b1-110">Plik jest mapowany na wykonanie, przy użyciu `LoadLibrary` funkcji lub `CreateFileMapping` funkcją `SEC_IMAGE` flagi.</span><span class="sxs-lookup"><span data-stu-id="1f3b1-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f3b1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f3b1-111">Requirements</span></span>  
 <span data-ttu-id="1f3b1-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f3b1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f3b1-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1f3b1-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1f3b1-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f3b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f3b1-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f3b1-115">See also</span></span>

- [<span data-ttu-id="1f3b1-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="1f3b1-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="1f3b1-117">GetFileMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="1f3b1-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
