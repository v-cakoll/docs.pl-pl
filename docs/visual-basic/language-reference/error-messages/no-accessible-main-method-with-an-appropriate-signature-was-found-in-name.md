---
title: W elemencie „<name>” nie odnaleziono dostępnej metody „Main” z odpowiednim podpisem.
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591972"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="0cffa-102">Brak metody dostępne "Main" z odpowiednim podpisem został znaleziony w "\<name >"</span><span class="sxs-lookup"><span data-stu-id="0cffa-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="0cffa-103">Aplikacje wiersza poleceń jest posiadanie `Sub Main` zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="0cffa-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="0cffa-104">`Main` musi być zadeklarowany jako `Public Shared` Jeśli jest zdefiniowana w klasie lub jako `Public` Jeśli zdefiniowany w module.</span><span class="sxs-lookup"><span data-stu-id="0cffa-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="0cffa-105">**Identyfikator błędu:** BC30737</span><span class="sxs-lookup"><span data-stu-id="0cffa-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0cffa-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0cffa-106">To correct this error</span></span>  
  
- <span data-ttu-id="0cffa-107">Zdefiniuj `Public Sub Main` procedury dla Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="0cffa-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="0cffa-108">Zadeklaruj go jako `Shared` tylko wtedy, gdy zdefiniujesz wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="0cffa-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cffa-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cffa-109">See also</span></span>

- [<span data-ttu-id="0cffa-110">Struktura programu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cffa-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="0cffa-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="0cffa-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
