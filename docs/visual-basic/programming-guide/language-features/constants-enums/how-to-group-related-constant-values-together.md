---
title: 'Porady: grupowanie związanych wartości stałych'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: d2393af8b0c2b0c2e528f9908a78fbc7f182c8cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414443"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="2758d-102">Porady: grupowanie związanych wartości stałych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2758d-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="2758d-103">Wyliczenie jest najlepszym sposobem grupowania powiązanych ze sobą stałych.</span><span class="sxs-lookup"><span data-stu-id="2758d-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="2758d-104">Wyliczenie można utworzyć przy użyciu `Enum` instrukcji w sekcji deklaracji klasy lub modułu.</span><span class="sxs-lookup"><span data-stu-id="2758d-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="2758d-105">Aby uzyskać więcej informacji, zobacz [How to: DECLARE a Enumeration](how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="2758d-105">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="2758d-106">Aby pogrupować powiązane wartości stałe</span><span class="sxs-lookup"><span data-stu-id="2758d-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="2758d-107">Napisz deklarację zawierającą poziom dostępu do kodu, `Enum` słowo kluczowe i prawidłową nazwę.</span><span class="sxs-lookup"><span data-stu-id="2758d-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="2758d-108">Ten przykład tworzy `Private` Wyliczenie `temperatureValues` .</span><span class="sxs-lookup"><span data-stu-id="2758d-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="2758d-109">Zdefiniuj stałe w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="2758d-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="2758d-110">Ten przykład tworzy `Public` Wyliczenie `temperatureValues` i przypisuje jego wartości.</span><span class="sxs-lookup"><span data-stu-id="2758d-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2758d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2758d-111">See also</span></span>

- [<span data-ttu-id="2758d-112">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="2758d-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="2758d-113">Porady: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2758d-113">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="2758d-114">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="2758d-114">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="2758d-115">Stałe — Przegląd</span><span class="sxs-lookup"><span data-stu-id="2758d-115">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="2758d-116">Stała i typy literałów</span><span class="sxs-lookup"><span data-stu-id="2758d-116">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="2758d-117">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2758d-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
