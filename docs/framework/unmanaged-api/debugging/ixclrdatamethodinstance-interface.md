---
title: IXCLRDataMethodInstance, interfejs
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c51825433bbc86c897c097475d5c15c855f6ec8b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790409"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="b0dcd-102">IXCLRDataMethodInstance, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0dcd-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="b0dcd-103">Zapewnia metody wykonywania zapytań dotyczących informacji o wystąpieniu metody.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="b0dcd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b0dcd-104">Methods</span></span>

| <span data-ttu-id="b0dcd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0dcd-105">Method</span></span>                                                                                                                  | <span data-ttu-id="b0dcd-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b0dcd-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="b0dcd-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="b0dcd-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="b0dcd-108">Pobiera informacje o mapowaniu IL to Address.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="b0dcd-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="b0dcd-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="b0dcd-110">Pobiera najbardziej reprezentatywny adres punktu wejścia dla natywnej kompilacji wszystkich możliwych punktów wejścia dla metody.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b0dcd-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0dcd-111">Remarks</span></span>

<span data-ttu-id="b0dcd-112">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b0dcd-113">Jest to jednak interfejs COM, który pochodzi od `IUnknown` z identyfikatorem GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5`, który można uzyskać za pomocą zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="b0dcd-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0dcd-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0dcd-114">Requirements</span></span>

<span data-ttu-id="b0dcd-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0dcd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b0dcd-116">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="b0dcd-116">**Header:** None</span></span>  
<span data-ttu-id="b0dcd-117">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="b0dcd-117">**Library:** None</span></span>  
<span data-ttu-id="b0dcd-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b0dcd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b0dcd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0dcd-119">See also</span></span>

- [<span data-ttu-id="b0dcd-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b0dcd-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="b0dcd-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b0dcd-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
