---
title: 'Porady: iterowanie za pomocą wyliczania w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646581"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="4fb28-102">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4fb28-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="4fb28-103">Wyliczenia oferują wygodny do pracy z zestawów powiązanych stałych i do skojarzenia z nazwami wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="4fb28-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="4fb28-104">Do iteracji wyliczenie, można go przenieść do tablicy przy użyciu <xref:System.Enum.GetValues%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4fb28-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="4fb28-105">Można również wykonać iterację przy użyciu wyliczania `For...Each` instrukcji, za pomocą <xref:System.Enum.GetNames%2A> lub <xref:System.Enum.GetValues%2A> metodę, aby wyodrębnić wartość ciągu lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="4fb28-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="4fb28-106">Aby wykonać iterację — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4fb28-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="4fb28-107">Deklarowanie tablicy i przekonwertować go z wyliczenia <xref:System.Enum.GetValues%2A> metoda przed przekazaniem tablicy jako użytkownik będzie innej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4fb28-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="4fb28-108">W poniższym przykładzie przedstawiono każdy element członkowski wyliczenia <xref:Microsoft.VisualBasic.FirstDayOfWeek> zgodnie z jego iterację wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4fb28-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4fb28-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fb28-109">See Also</span></span>  
 [<span data-ttu-id="4fb28-110">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="4fb28-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="4fb28-111">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="4fb28-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="4fb28-112">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="4fb28-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="4fb28-113">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4fb28-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="4fb28-114">Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4fb28-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="4fb28-115">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="4fb28-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="4fb28-116">Tablice</span><span class="sxs-lookup"><span data-stu-id="4fb28-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
