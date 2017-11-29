---
title: "Porady: tworzenie ciągów za pomocą StringBuilder w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c799794b319843b0239ce9589e0c556c603c8617
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="d7715-102">Porady: tworzenie ciągów za pomocą StringBuilder w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7715-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="d7715-103">Ten przykład tworzy ciąg z dużo mniejszym ciągów za pomocą <xref:System.Text.StringBuilder> klasy.</span><span class="sxs-lookup"><span data-stu-id="d7715-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="d7715-104"><xref:System.Text.StringBuilder> Klasy jest bardziej efektywne niż `&=` operator łączenie wielu ciągów.</span><span class="sxs-lookup"><span data-stu-id="d7715-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7715-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7715-105">Example</span></span>  
 <span data-ttu-id="d7715-106">Poniższy przykład tworzy wystąpienie <xref:System.Text.StringBuilder> klasy, dołącza 1000 ciągi do tego wystąpienia, a następnie zwraca reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="d7715-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d7715-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7715-107">See Also</span></span>  
 [<span data-ttu-id="d7715-108">Używanie klasy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="d7715-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="d7715-109">& = — operator</span><span class="sxs-lookup"><span data-stu-id="d7715-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="d7715-110">Ciągi</span><span class="sxs-lookup"><span data-stu-id="d7715-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="d7715-111">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="d7715-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="d7715-112">Manipulowanie ciągami</span><span class="sxs-lookup"><span data-stu-id="d7715-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 [<span data-ttu-id="d7715-113">Przykładowe ciągów</span><span class="sxs-lookup"><span data-stu-id="d7715-113">Strings Sample</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)
