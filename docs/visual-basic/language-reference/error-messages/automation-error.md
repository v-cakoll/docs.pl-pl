---
title: Błąd automatyzacji
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 8370f744b916ce4a797c808ed58c5fc9580e6278
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304315"
---
# <a name="automation-error"></a><span data-ttu-id="f4dd7-102">Błąd automatyzacji</span><span class="sxs-lookup"><span data-stu-id="f4dd7-102">Automation error</span></span>
<span data-ttu-id="f4dd7-103">Wystąpił błąd podczas wykonywania metody lub pobieranie lub ustawianie właściwości zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4dd7-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="f4dd7-104">Ten błąd został zgłoszony przez aplikację, który utworzył obiekt.</span><span class="sxs-lookup"><span data-stu-id="f4dd7-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4dd7-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f4dd7-105">To correct this error</span></span>  
  
1. <span data-ttu-id="f4dd7-106">Sprawdź właściwości `Err` obiektu w celu ustalenia źródła i charakteru błędu.</span><span class="sxs-lookup"><span data-stu-id="f4dd7-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="f4dd7-107">Użyj `On Error Resume Next` instrukcję tuż przed uzyskiwania dostępu do instrukcji i sprawdź, czy błędy bezpośrednio po uzyskiwania dostępu do instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f4dd7-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4dd7-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4dd7-108">See also</span></span>

- [<span data-ttu-id="f4dd7-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="f4dd7-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="f4dd7-110">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="f4dd7-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
