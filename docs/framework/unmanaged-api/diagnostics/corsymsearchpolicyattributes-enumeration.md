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
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178348"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="c9f55-102">CorSymSearchPolicyAttributes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c9f55-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="c9f55-103">Określa zasady, które mają być używane podczas wyszukiwania czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="c9f55-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="c9f55-104">Te stałe są używane przez [metody ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) i [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c9f55-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c9f55-105">Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych programu (PDB) z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="c9f55-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f55-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9f55-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="c9f55-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c9f55-107">Members</span></span>  
  
|<span data-ttu-id="c9f55-108">Członek</span><span class="sxs-lookup"><span data-stu-id="c9f55-108">Member</span></span>|<span data-ttu-id="c9f55-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c9f55-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="c9f55-110">Wysyła zapytanie do rejestru o ścieżki wyszukiwania symboli.</span><span class="sxs-lookup"><span data-stu-id="c9f55-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="c9f55-111">Uzyskuje dostęp do serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="c9f55-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="c9f55-112">Przeszukuje ścieżkę określoną w katalogu debugowania.</span><span class="sxs-lookup"><span data-stu-id="c9f55-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="c9f55-113">Wyszukuje bazę danych WDB w miejscu, w którym znajduje się plik exe.</span><span class="sxs-lookup"><span data-stu-id="c9f55-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9f55-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9f55-114">Requirements</span></span>  
 <span data-ttu-id="c9f55-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9f55-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f55-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9f55-116">See also</span></span>

- [<span data-ttu-id="c9f55-117">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c9f55-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
