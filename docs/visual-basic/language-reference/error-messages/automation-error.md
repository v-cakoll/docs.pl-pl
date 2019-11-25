---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: df153167bc8c73a2d3760c8d7db30dccfa468e35
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976146"
---
# <a name="automation-error"></a><span data-ttu-id="a28ca-102">Błąd automatyzacji</span><span class="sxs-lookup"><span data-stu-id="a28ca-102">Automation error</span></span>

<span data-ttu-id="a28ca-103">Wystąpił błąd podczas wykonywania metody lub pobierania lub ustawiania właściwości zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="a28ca-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="a28ca-104">Błąd został zgłoszony przez aplikację, która utworzyła obiekt.</span><span class="sxs-lookup"><span data-stu-id="a28ca-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a28ca-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a28ca-105">To correct this error</span></span>  
  
1. <span data-ttu-id="a28ca-106">Sprawdź właściwości obiektu `Err`, aby określić źródło i charakter błędu.</span><span class="sxs-lookup"><span data-stu-id="a28ca-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="a28ca-107">Użyj instrukcji `On Error Resume Next` bezpośrednio przed instrukcją dostępu, a następnie wyewidencjonuj błędy bezpośrednio po instrukcji dostępu.</span><span class="sxs-lookup"><span data-stu-id="a28ca-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a28ca-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a28ca-108">See also</span></span>

- [<span data-ttu-id="a28ca-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="a28ca-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="a28ca-110">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="a28ca-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
