---
title: "CorSymSearchPolicyAttributes — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc1bef8c393a7778c194b2d4d45c3abdb583fecf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="619ab-102">CorSymSearchPolicyAttributes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="619ab-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="619ab-103">Określa zasady do użycia podczas wyszukiwania dla czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="619ab-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="619ab-104">Stałe te są używane przez [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) i [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="619ab-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="619ab-105">Jest to zagrożenie, aby otworzyć plik programu (PDB) bazy danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="619ab-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="619ab-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="619ab-106">Syntax</span></span>  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="619ab-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="619ab-107">Members</span></span>  
  
|<span data-ttu-id="619ab-108">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="619ab-108">Member</span></span>|<span data-ttu-id="619ab-109">Opis</span><span class="sxs-lookup"><span data-stu-id="619ab-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="619ab-110">Wysyła zapytanie do rejestru dla ścieżki wyszukiwania symboli.</span><span class="sxs-lookup"><span data-stu-id="619ab-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="619ab-111">Uzyskuje dostęp do serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="619ab-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="619ab-112">Wyszukuje ścieżka określona w katalogu debugowania.</span><span class="sxs-lookup"><span data-stu-id="619ab-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="619ab-113">Wyszukuje PDB w miejscu, w którym się plik .exe.</span><span class="sxs-lookup"><span data-stu-id="619ab-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="619ab-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="619ab-114">Requirements</span></span>  
 <span data-ttu-id="619ab-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="619ab-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="619ab-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="619ab-116">See Also</span></span>  
 [<span data-ttu-id="619ab-117">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="619ab-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
