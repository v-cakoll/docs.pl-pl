---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 25c3b71eb818223c58ab17d9be885033a5d4ded0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197032"
---
# <a name="automation-error"></a><span data-ttu-id="a779e-102">Błąd automatyzacji</span><span class="sxs-lookup"><span data-stu-id="a779e-102">Automation error</span></span>
<span data-ttu-id="a779e-103">Wystąpił błąd podczas wykonywania metody lub pobierania lub ustawiania właściwości zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="a779e-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="a779e-104">Błąd został zgłoszony przez aplikację, która utworzyła obiekt.</span><span class="sxs-lookup"><span data-stu-id="a779e-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a779e-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a779e-105">To correct this error</span></span>  
  
1. <span data-ttu-id="a779e-106">Sprawdź właściwości obiektu `Err`, aby określić źródło i charakter błędu.</span><span class="sxs-lookup"><span data-stu-id="a779e-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="a779e-107">Użyj instrukcji `On Error Resume Next` bezpośrednio przed instrukcją dostępu, a następnie wyewidencjonuj błędy bezpośrednio po instrukcji dostępu.</span><span class="sxs-lookup"><span data-stu-id="a779e-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a779e-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a779e-108">See also</span></span>

- [<span data-ttu-id="a779e-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="a779e-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="a779e-110">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="a779e-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
