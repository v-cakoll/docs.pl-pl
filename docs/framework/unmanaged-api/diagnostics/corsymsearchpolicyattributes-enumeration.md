---
title: CorSymSearchPolicyAttributes — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7188c516d3d0a5192251697ec743e9d41f8d9072
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913742"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="5163c-102">CorSymSearchPolicyAttributes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5163c-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="5163c-103">Określa zasady, które mają być używane podczas wyszukiwania czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="5163c-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="5163c-104">Te stałe są używane przez metody [ISymUnmanagedBinder2:: GetReaderForFile2 —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) i [ISymUnmanagedBinder3:: GetReaderFromCallback —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5163c-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5163c-105">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="5163c-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5163c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5163c-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="5163c-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5163c-107">Members</span></span>  
  
|<span data-ttu-id="5163c-108">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5163c-108">Member</span></span>|<span data-ttu-id="5163c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5163c-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="5163c-110">Wysyła zapytanie do rejestru pod kątem ścieżek wyszukiwania symboli.</span><span class="sxs-lookup"><span data-stu-id="5163c-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="5163c-111">Uzyskuje dostęp do serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="5163c-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="5163c-112">Przeszukuje ścieżkę określoną w katalogu debugowania.</span><span class="sxs-lookup"><span data-stu-id="5163c-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="5163c-113">Wyszukuje PDB w miejscu, gdzie plik. exe jest.</span><span class="sxs-lookup"><span data-stu-id="5163c-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5163c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5163c-114">Requirements</span></span>  
 <span data-ttu-id="5163c-115">**Nagłówki** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5163c-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5163c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5163c-116">See also</span></span>

- [<span data-ttu-id="5163c-117">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="5163c-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
