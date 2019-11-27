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
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448732"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="de4cd-102">EnumImportTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="de4cd-102">EnumImportTypes Method</span></span>

<span data-ttu-id="de4cd-103">Wylicza każdy typ w każdym zakresie.</span><span class="sxs-lookup"><span data-stu-id="de4cd-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="de4cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de4cd-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="de4cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de4cd-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="de4cd-106">Dojście do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="de4cd-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="de4cd-107">Maksymalna liczba typów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="de4cd-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="de4cd-108">Odbiera tokeny typu, które nie przekraczają `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="de4cd-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="de4cd-109">Odbiera rzeczywistą liczbę typów w `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="de4cd-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="de4cd-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="de4cd-110">Return Value</span></span>

<span data-ttu-id="de4cd-111">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="de4cd-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="de4cd-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de4cd-112">Requirements</span></span>

<span data-ttu-id="de4cd-113">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="de4cd-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="de4cd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de4cd-114">See also</span></span>

- [<span data-ttu-id="de4cd-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="de4cd-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="de4cd-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="de4cd-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="de4cd-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="de4cd-117">ALink API</span></span>](index.md)
