---
title: "Porady: konwertowanie ciągu do tablicy znaków w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59d0da52c8f78b93c76325e6242156c106deeaf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="3de21-102">Porady: konwertowanie ciągu do tablicy znaków w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3de21-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="3de21-103">Czasami jest przydatne do danych o znaki w ciągu i pozycje te znaki w ciągu, na przykład gdy są analizowania parametrów.</span><span class="sxs-lookup"><span data-stu-id="3de21-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="3de21-104">W tym przykładzie pokazano, jak wprowadzasz tablicy znaków w ciągu wywołując ciąg <xref:System.String.ToCharArray%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3de21-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3de21-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3de21-105">Example</span></span>  
 <span data-ttu-id="3de21-106">W tym przykładzie pokazano, jak podzielić ciąg do `Char` tablicy i dzielenia ciąg do `String` tablicy jego znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="3de21-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="3de21-107">Przyczyna tej różnicy to, że znaków Unicode może składać się z co najmniej dwóch `Char` znaków (np. para zastępcza lub łączenie sekwencja znaków).</span><span class="sxs-lookup"><span data-stu-id="3de21-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="3de21-108">Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.TextElementEnumerator> i "Unicode Standard" w http://www.unicode.org.</span><span class="sxs-lookup"><span data-stu-id="3de21-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and "The Unicode Standard" at http://www.unicode.org.</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="3de21-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3de21-109">Example</span></span>  
 <span data-ttu-id="3de21-110">Trudniej podzielić ciąg na jego znaków Unicode, ale jest to konieczne, jeśli potrzebujesz informacji na temat wizualną reprezentację ciągu.</span><span class="sxs-lookup"><span data-stu-id="3de21-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="3de21-111">W tym przykładzie użyto <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodę, aby uzyskać informacje na temat wchodzące w skład ciąg znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="3de21-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3de21-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3de21-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="3de21-113">Porady: dostęp do znaków w ciągach</span><span class="sxs-lookup"><span data-stu-id="3de21-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="3de21-114">Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3de21-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="3de21-115">Ciągi</span><span class="sxs-lookup"><span data-stu-id="3de21-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
