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
ms.openlocfilehash: 0b1c982b25af9edea76a038b4314b4bd608f07df
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420893"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="ce4b5-102">IXCLRDataMethodInstance, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce4b5-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="ce4b5-103">Zapewnia metody wykonywania zapytań dotyczących informacji o wystąpieniu metody.</span><span class="sxs-lookup"><span data-stu-id="ce4b5-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ce4b5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ce4b5-104">Methods</span></span>

| <span data-ttu-id="ce4b5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ce4b5-105">Method</span></span>                                                                                                                  | <span data-ttu-id="ce4b5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ce4b5-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="ce4b5-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="ce4b5-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="ce4b5-108">Pobiera informacje o mapowaniu IL to Address.</span><span class="sxs-lookup"><span data-stu-id="ce4b5-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="ce4b5-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="ce4b5-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="ce4b5-110">Pobiera najbardziej reprezentatywny adres punktu wejścia dla natywnej kompilacji wszystkich możliwych punktów wejścia dla metody.</span><span class="sxs-lookup"><span data-stu-id="ce4b5-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ce4b5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce4b5-111">Remarks</span></span>

<span data-ttu-id="ce4b5-112">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="ce4b5-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ce4b5-113">Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , który można uzyskać za pomocą zwykłych mechanizmów com.</span><span class="sxs-lookup"><span data-stu-id="ce4b5-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ce4b5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce4b5-114">Requirements</span></span>

<span data-ttu-id="ce4b5-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce4b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ce4b5-116">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ce4b5-116">**Header:** None</span></span>  
<span data-ttu-id="ce4b5-117">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ce4b5-117">**Library:** None</span></span>  
<span data-ttu-id="ce4b5-118">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ce4b5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ce4b5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce4b5-119">See also</span></span>

- [<span data-ttu-id="ce4b5-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ce4b5-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="ce4b5-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ce4b5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
