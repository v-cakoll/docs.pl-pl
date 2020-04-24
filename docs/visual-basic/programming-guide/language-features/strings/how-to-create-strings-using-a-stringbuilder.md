---
title: 'Jak: tworzenie ciągów za pomocą Kreatora ciągów'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645330"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="3073f-102">Jak: tworzenie ciągów przy użyciu Kreatora ciągów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3073f-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="3073f-103">W tym przykładzie tworzy długi ciąg z <xref:System.Text.StringBuilder> wielu mniejszych ciągów przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="3073f-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="3073f-104">Klasa <xref:System.Text.StringBuilder> jest bardziej wydajne niż `&=` operator do łączenia wielu ciągów.</span><span class="sxs-lookup"><span data-stu-id="3073f-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="3073f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3073f-105">Example</span></span>

<span data-ttu-id="3073f-106">Poniższy przykład tworzy wystąpienie <xref:System.Text.StringBuilder> klasy, dołącza 1000 ciągów do tego wystąpienia, a następnie zwraca jego reprezentację ciągu:</span><span class="sxs-lookup"><span data-stu-id="3073f-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="3073f-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3073f-107">See also</span></span>

- [<span data-ttu-id="3073f-108">Używanie klasy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="3073f-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="3073f-109">&= Operator</span><span class="sxs-lookup"><span data-stu-id="3073f-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="3073f-110">Ciągi</span><span class="sxs-lookup"><span data-stu-id="3073f-110">Strings</span></span>](index.md)
- [<span data-ttu-id="3073f-111">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="3073f-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="3073f-112">Manipulowanie ciągami</span><span class="sxs-lookup"><span data-stu-id="3073f-112">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
