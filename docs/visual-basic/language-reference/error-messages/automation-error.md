---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: fdd77510d03cd9e5228be1ba9ec9f746dcc0dfe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="automation-error"></a><span data-ttu-id="6a1a4-102">Błąd automatyzacji</span><span class="sxs-lookup"><span data-stu-id="6a1a4-102">Automation error</span></span>
<span data-ttu-id="6a1a4-103">Wystąpił błąd podczas wykonywania metody lub pobierania lub ustawiania właściwości zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a1a4-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="6a1a4-104">Błąd został zgłoszony przez aplikację, który utworzył obiekt.</span><span class="sxs-lookup"><span data-stu-id="6a1a4-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a1a4-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6a1a4-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="6a1a4-106">Sprawdź właściwości `Err` obiektem, aby określić źródło i charakteru błędu.</span><span class="sxs-lookup"><span data-stu-id="6a1a4-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="6a1a4-107">Użyj `On Error Resume Next` instrukcji bezpośrednio przed podczas uzyskiwania dostępu do instrukcji, a następnie Wyszukaj błędy bezpośrednio po instrukcji podczas uzyskiwania dostępu do.</span><span class="sxs-lookup"><span data-stu-id="6a1a4-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1a4-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a1a4-108">See Also</span></span>  
 [<span data-ttu-id="6a1a4-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="6a1a4-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="6a1a4-110">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="6a1a4-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
