---
title: CorOpenFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 831f4665967f2cd07a7ebb4de750fbe456a82261
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781687"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="d0a5e-102">CorOpenFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d0a5e-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="d0a5e-103">Zawiera wartości flagi, które kontrolują zachowanie metadanych podczas otwierania plików manifestu.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0a5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0a5e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d0a5e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0a5e-105">Members</span></span>  
  
|<span data-ttu-id="d0a5e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d0a5e-106">Member</span></span>|<span data-ttu-id="d0a5e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d0a5e-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="d0a5e-108">Wskazuje, czy można otworzyć pliku do odczytu tylko.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="d0a5e-109">Wskazuje, że plik powinien zostać otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="d0a5e-110">Jeśli używasz `ofWrite` Flaga podczas otwierania pliku winmd, należy także przekazać `ofNoTransform` flagi.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="d0a5e-111">Maska do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="d0a5e-112">Wskazuje, że można odczytać pliku do pamięci.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="d0a5e-113">Metadane należy zachować własną kopię.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="d0a5e-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-114">Obsolete.</span></span> <span data-ttu-id="d0a5e-115">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="d0a5e-116">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-116">Obsolete.</span></span> <span data-ttu-id="d0a5e-117">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="d0a5e-118">Wskazuje, że dla odczytu, które można otworzyć pliku wywołanie `QueryInterface` dla [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nie może zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="d0a5e-119">Wskazuje, że pamięć została przydzielona za pomocą wywołania [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) i zostanie zwolniona w metadanych.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="d0a5e-120">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-120">Obsolete.</span></span> <span data-ttu-id="d0a5e-121">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="d0a5e-122">Wskazuje, należy wyłączyć automatyczne transformacje plików winmd.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="d0a5e-123">Innymi słowy należy wyłączyć projekcji typu środowiska wykonawczego Windows, aby typ .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="d0a5e-124">Aby uzyskać więcej informacji, zobacz [środowiska uruchomieniowego Windows i środowisko CLR - poniżej składniki przy użyciu platformy .NET i środowiska wykonawczego Windows](https://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="d0a5e-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="d0a5e-125">Zarezerwowane do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="d0a5e-126">Zarezerwowane do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="d0a5e-127">Zarezerwowane do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d0a5e-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0a5e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0a5e-128">Requirements</span></span>  
 <span data-ttu-id="d0a5e-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0a5e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0a5e-130">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d0a5e-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d0a5e-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0a5e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a5e-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0a5e-132">See also</span></span>

- [<span data-ttu-id="d0a5e-133">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d0a5e-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
