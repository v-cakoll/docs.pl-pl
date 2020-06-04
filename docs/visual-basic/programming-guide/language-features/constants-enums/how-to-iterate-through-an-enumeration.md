---
title: 'Instrukcje: iterowanie za pomocą wyliczania'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414430"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="8704a-102">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8704a-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="8704a-103">Wyliczenia zapewniają wygodny sposób pracy z zestawami powiązanych stałych i kojarzenia wartości stałych z nazwami.</span><span class="sxs-lookup"><span data-stu-id="8704a-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="8704a-104">Aby wykonać iterację wyliczenia, można przenieść go do tablicy przy użyciu <xref:System.Enum.GetValues%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8704a-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="8704a-105">Można również wykonać iterację w wyliczeniu przy użyciu `For...Each` instrukcji, <xref:System.Enum.GetNames%2A> używając <xref:System.Enum.GetValues%2A> metody lub do wyodrębnienia ciągu lub wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="8704a-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="8704a-106">Aby wykonać iterację wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8704a-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="8704a-107">Zadeklaruj tablicę i przekonwertuj jej Wyliczenie na <xref:System.Enum.GetValues%2A> metodę przed przekazaniem tablicy, tak jak każda inna zmienna.</span><span class="sxs-lookup"><span data-stu-id="8704a-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="8704a-108">Poniższy przykład wyświetla każdy element członkowski wyliczenia <xref:Microsoft.VisualBasic.FirstDayOfWeek> podczas iteracji przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="8704a-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="8704a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8704a-109">See also</span></span>

- [<span data-ttu-id="8704a-110">Enumerations — Przegląd</span><span class="sxs-lookup"><span data-stu-id="8704a-110">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="8704a-111">Instrukcje: deklarowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8704a-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="8704a-112">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="8704a-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="8704a-113">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8704a-113">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="8704a-114">Porady: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8704a-114">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="8704a-115">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="8704a-115">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="8704a-116">Tablice</span><span class="sxs-lookup"><span data-stu-id="8704a-116">Arrays</span></span>](../arrays/index.md)
