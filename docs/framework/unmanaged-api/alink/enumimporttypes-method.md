---
title: EnumImportTypes — Metoda
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355743"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="36390-102">EnumImportTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="36390-102">EnumImportTypes Method</span></span>

<span data-ttu-id="36390-103">Wylicza każdy typ w każdym zakresem.</span><span class="sxs-lookup"><span data-stu-id="36390-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="36390-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36390-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="36390-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36390-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="36390-106">Dojście dla typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="36390-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="36390-107">Maksymalna liczba typów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="36390-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="36390-108">Odbiera tokeny typu, aby nie przekroczyć `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="36390-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="36390-109">Odbiera rzeczywista liczba wpisz `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="36390-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="36390-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="36390-110">Return Value</span></span>

<span data-ttu-id="36390-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="36390-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="36390-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36390-112">Requirements</span></span>

<span data-ttu-id="36390-113">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="36390-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="36390-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36390-114">See also</span></span>

- [<span data-ttu-id="36390-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="36390-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="36390-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="36390-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="36390-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="36390-117">ALink API</span></span>](index.md)