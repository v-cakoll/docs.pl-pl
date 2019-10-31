---
title: Klasa nie obsługuje automatyzacji lub oczekiwanego interfejsu
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: d249648748249af438ee6228cccc8e74f68407fb
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197530"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="459ad-102">Klasa nie obsługuje automatyzacji lub oczekiwanego interfejsu</span><span class="sxs-lookup"><span data-stu-id="459ad-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="459ad-103">Klasa określona w wywołaniu funkcji `GetObject` lub `CreateObject` nie uwidacznia interfejsu programowalności lub zmieniono projekt z. dll na. exe lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="459ad-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="459ad-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="459ad-104">To correct this error</span></span>  
  
1. <span data-ttu-id="459ad-105">Zapoznaj się z dokumentacją aplikacji, która utworzyła obiekt, aby uzyskać ograniczenia dotyczące używania automatyzacji z tą klasą obiektów.</span><span class="sxs-lookup"><span data-stu-id="459ad-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="459ad-106">Jeśli projekt został zmieniony z. dll na. exe lub odwrotnie, należy ręcznie wyrejestrować stary plik. dll lub. exe.</span><span class="sxs-lookup"><span data-stu-id="459ad-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459ad-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="459ad-107">See also</span></span>

- [<span data-ttu-id="459ad-108">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="459ad-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="459ad-109">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="459ad-109">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
