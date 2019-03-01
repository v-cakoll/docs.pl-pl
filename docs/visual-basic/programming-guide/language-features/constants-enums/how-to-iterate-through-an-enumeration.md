---
title: 'Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: dd7a540839fd833d3a316506e433c576edae5384
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979089"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="9fd12-102">Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fd12-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="9fd12-103">Wyliczenia zapewniają wygodny sposób pracy z zestawami pokrewnych stałych i skojarzyć wartości stałych o nazwach.</span><span class="sxs-lookup"><span data-stu-id="9fd12-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="9fd12-104">Do iteracji, za pomocą wyliczania, można go przenieść do tablicy przy użyciu <xref:System.Enum.GetValues%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9fd12-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="9fd12-105">Można również wykonać iterację przy użyciu wyliczenia `For...Each` instrukcji, za pomocą <xref:System.Enum.GetNames%2A> lub <xref:System.Enum.GetValues%2A> metodę, aby uzyskać wartość ciągu lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="9fd12-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="9fd12-106">Do iteracji przez wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9fd12-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="9fd12-107">Deklarowanie tablicy i przekonwertować ją za pomocą wyliczenia <xref:System.Enum.GetValues%2A> metoda przed przekazaniem tablicy, jak będą inne zmienne.</span><span class="sxs-lookup"><span data-stu-id="9fd12-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="9fd12-108">Poniższy przykład wyświetla każdy element członkowski wyliczenia <xref:Microsoft.VisualBasic.FirstDayOfWeek> jako iteruje wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9fd12-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="9fd12-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fd12-109">See also</span></span>
- [<span data-ttu-id="9fd12-110">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="9fd12-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="9fd12-111">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="9fd12-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="9fd12-112">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="9fd12-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="9fd12-113">Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9fd12-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="9fd12-114">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9fd12-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="9fd12-115">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="9fd12-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="9fd12-116">Tablice</span><span class="sxs-lookup"><span data-stu-id="9fd12-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
