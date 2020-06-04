---
title: Klasy zarządzane pochodne od klasy COM nie mogą być wywoływane z późnym wiązaniem.
ms.date: 07/20/2015
f1_keywords:
- vbrLateboundCallToInheritedComClass
ms.assetid: 7bc16e84-8d29-4f8e-bc4f-002c65c71099
ms.openlocfilehash: 401cb5d7194cbef616c87d59e5b1ed7f923fe6f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402125"
---
# <a name="managed-classes-derived-from-a-com-class-cannot-be-called-late-bound"></a><span data-ttu-id="dd25e-102">Klasy zarządzane pochodne od klasy COM nie mogą być wywoływane z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="dd25e-102">Managed classes derived from a COM class cannot be called late-bound.</span></span>

<span data-ttu-id="dd25e-103">Podjęto próbę wykonania wywołania z późnym wiązaniem do klasy zarządzanej pochodzącej od klasy COM; takie wywołania nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dd25e-103">You attempted to make a late-bound call to a managed class derived from a COM Class; such calls are not supported.</span></span>

## <a name="to-correct-the-problem"></a><span data-ttu-id="dd25e-104">Aby rozwiązać ten problem</span><span class="sxs-lookup"><span data-stu-id="dd25e-104">To correct the problem</span></span>

<span data-ttu-id="dd25e-105">Utwórz wczesne powiązanie wywołania.</span><span class="sxs-lookup"><span data-stu-id="dd25e-105">Make the call early bound.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd25e-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd25e-106">See also</span></span>

- [<span data-ttu-id="dd25e-107">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="dd25e-107">Error Types</span></span>](../programming-guide/language-features/error-types.md)
