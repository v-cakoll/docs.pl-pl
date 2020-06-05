---
title: Procedura lub funkcja nie jest zdefiniowana
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 9eb13d943f9f1cffc984847f7339111e06f5aa6b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373930"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="a7f4b-102">Procedura lub funkcja nie jest zdefiniowana</span><span class="sxs-lookup"><span data-stu-id="a7f4b-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="a7f4b-103">A `Sub` lub `Function` musi być zdefiniowana, aby można było ją wywołać.</span><span class="sxs-lookup"><span data-stu-id="a7f4b-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="a7f4b-104">Możliwe przyczyny tego błędu to:</span><span class="sxs-lookup"><span data-stu-id="a7f4b-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="a7f4b-105">Błędna pisownia nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="a7f4b-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="a7f4b-106">Próba wywołania procedury z innego projektu bez jawnego dodania odwołania do tego projektu w oknie dialogowym **odwołania** .</span><span class="sxs-lookup"><span data-stu-id="a7f4b-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="a7f4b-107">Określanie procedury, która nie jest widoczna dla procedury wywołującej.</span><span class="sxs-lookup"><span data-stu-id="a7f4b-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="a7f4b-108">Deklarowanie procedury biblioteki dołączanej dynamicznie (DLL) systemu Windows lub procedury kodu dla systemu Macintosh, która nie znajduje się w określonej bibliotece lub zasobie kodu.</span><span class="sxs-lookup"><span data-stu-id="a7f4b-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7f4b-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a7f4b-109">To correct this error</span></span>  
  
1. <span data-ttu-id="a7f4b-110">Upewnij się, że nazwa procedury jest wpisana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="a7f4b-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="a7f4b-111">Znajdź nazwę projektu zawierającego procedurę, która ma zostać wywołana, w oknie dialogowym **odwołania** .</span><span class="sxs-lookup"><span data-stu-id="a7f4b-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="a7f4b-112">Jeśli nie jest wyświetlany, kliknij przycisk **Przeglądaj** , aby go wyszukać.</span><span class="sxs-lookup"><span data-stu-id="a7f4b-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="a7f4b-113">Zaznacz pole wyboru po lewej stronie nazwy projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7f4b-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="a7f4b-114">Sprawdź nazwę procedury.</span><span class="sxs-lookup"><span data-stu-id="a7f4b-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f4b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7f4b-115">See also</span></span>

- [<span data-ttu-id="a7f4b-116">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="a7f4b-116">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="a7f4b-117">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="a7f4b-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="a7f4b-118">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a7f4b-118">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="a7f4b-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a7f4b-119">Function Statement</span></span>](../statements/function-statement.md)
