---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: d62ba57db8bffefb2cfebed705251d87fe285602
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409897"
---
# <a name="automation-error"></a><span data-ttu-id="cc5c3-102">Błąd automatyzacji</span><span class="sxs-lookup"><span data-stu-id="cc5c3-102">Automation error</span></span>

<span data-ttu-id="cc5c3-103">Wystąpił błąd podczas wykonywania metody lub pobierania lub ustawiania właściwości zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc5c3-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="cc5c3-104">Błąd został zgłoszony przez aplikację, która utworzyła obiekt.</span><span class="sxs-lookup"><span data-stu-id="cc5c3-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc5c3-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cc5c3-105">To correct this error</span></span>  
  
1. <span data-ttu-id="cc5c3-106">Sprawdź właściwości `Err` obiektu, aby określić źródło i charakter błędu.</span><span class="sxs-lookup"><span data-stu-id="cc5c3-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="cc5c3-107">Użyj `On Error Resume Next` instrukcji bezpośrednio przed instrukcją dostępu, a następnie wyewidencjonuj błędy natychmiast po instrukcji uzyskiwania dostępu.</span><span class="sxs-lookup"><span data-stu-id="cc5c3-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc5c3-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc5c3-108">See also</span></span>

- [<span data-ttu-id="cc5c3-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="cc5c3-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="cc5c3-110">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="cc5c3-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
