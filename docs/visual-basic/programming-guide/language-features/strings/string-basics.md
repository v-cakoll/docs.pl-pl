---
title: "Podstawowe informacje o ciągach w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8881ad6ab7f28689019463abdab3b867e010d51e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="fd864-102">Podstawowe informacje o ciągach w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd864-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="fd864-103">`String` — Typ danych reprezentuje ciąg znaków (każdy reprezentuje z kolei wystąpienia `Char` typu danych).</span><span class="sxs-lookup"><span data-stu-id="fd864-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="fd864-104">W tym temacie wprowadzono podstawowe pojęcia ciągów w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd864-104">This topic introduces the basic concepts of strings in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="fd864-105">Zmiennych ciągu</span><span class="sxs-lookup"><span data-stu-id="fd864-105">String Variables</span></span>  
 <span data-ttu-id="fd864-106">Wystąpienie ciągu można przypisać wartość literału, która reprezentuje ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="fd864-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="fd864-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fd864-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 <span data-ttu-id="fd864-108">A `String` zmiennej także zaakceptować wyrażeń na ciąg.</span><span class="sxs-lookup"><span data-stu-id="fd864-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="fd864-109">Odpowiednie przykłady przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="fd864-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 <span data-ttu-id="fd864-110">Wszelkie literal, która jest przypisana do `String` zmiennej musi być ujęta w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="fd864-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="fd864-111">Oznacza to, że znak cudzysłowu w ciągu nie może być reprezentowany przez znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="fd864-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="fd864-112">Na przykład następujący kod powoduje błąd kompilatora:</span><span class="sxs-lookup"><span data-stu-id="fd864-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 <span data-ttu-id="fd864-113">Ten kod powoduje błąd, ponieważ ciąg kompilator kończy się po drugim znaku cudzysłowu, a w pozostałej części ciąg jest interpretowany jako kod.</span><span class="sxs-lookup"><span data-stu-id="fd864-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="fd864-114">Aby rozwiązać ten problem, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] będą interpretowane przez dwa znaki cudzysłowu w ciągu literałów jako jeden znak cudzysłowu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="fd864-114">To solve this problem, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="fd864-115">W poniższym przykładzie pokazano prawidłowy sposób, aby uwzględnić znak cudzysłowu w ciągu:</span><span class="sxs-lookup"><span data-stu-id="fd864-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 <span data-ttu-id="fd864-116">W powyższym przykładzie dwa znaki cudzysłowu poprzedzających wyraz `Look` stają się jeden znak cudzysłowu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="fd864-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="fd864-117">Trzy cudzysłów na końcu wiersza reprezentuje jeden znak cudzysłowu w ciągu i znaków zakończenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="fd864-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="fd864-118">Literały ciągu może zawierać wiele wierszy:</span><span class="sxs-lookup"><span data-stu-id="fd864-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="fd864-119">Wynikowy ciąg zawiera sekwencje znaków nowego wiersza, używane w ciągu literału (vbcr, vbcrlf itp.).</span><span class="sxs-lookup"><span data-stu-id="fd864-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="fd864-120">Nie trzeba używać starego obejście problemu:</span><span class="sxs-lookup"><span data-stu-id="fd864-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="fd864-121">Znaków w ciągach</span><span class="sxs-lookup"><span data-stu-id="fd864-121">Characters in Strings</span></span>  
 <span data-ttu-id="fd864-122">Ciąg można traktować jako serię `Char` wartości i `String` typ ma wbudowane funkcje, które umożliwiają wykonywanie wielu manipulacje na ciąg, podobne manipulacje dozwoloną tablic.</span><span class="sxs-lookup"><span data-stu-id="fd864-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="fd864-123">Tak jak wszystkie tablicy w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], są tablice liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="fd864-123">Like all array in [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="fd864-124">Użytkownik może odwoływać się do określonego znaku w ciągu za pośrednictwem `Chars` właściwość, która umożliwia dostęp do znaków według pozycji, w których występuje w ciągu.</span><span class="sxs-lookup"><span data-stu-id="fd864-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="fd864-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fd864-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 <span data-ttu-id="fd864-126">W powyższym przykładzie `Chars` właściwości ciągu zwraca czwarte znak w ciągu jest `D`, a następnie przypisuje go do `myChar`.</span><span class="sxs-lookup"><span data-stu-id="fd864-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="fd864-127">Można także uzyskać długość ciągu określonego za pomocą `Length` właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd864-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="fd864-128">Jeśli musisz wykonać wiele manipulacje typ tablicy na ciąg można przekonwertować go na tablicę `Char` wystąpienia przy użyciu `ToCharArray` funkcja ciągu.</span><span class="sxs-lookup"><span data-stu-id="fd864-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="fd864-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fd864-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 <span data-ttu-id="fd864-130">Zmienna `myArray` teraz zawiera tablicę `Char` wartości reprezentującą znak ze `myString`.</span><span class="sxs-lookup"><span data-stu-id="fd864-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="fd864-131">Immutability ciągów</span><span class="sxs-lookup"><span data-stu-id="fd864-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="fd864-132">Ciąg jest *niezmienialnych*, co oznacza, że jego wartość nie można zmienić po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="fd864-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="fd864-133">Jednak to nie uniemożliwiają przypisywanie więcej niż jedną wartość zmiennej ciągu.</span><span class="sxs-lookup"><span data-stu-id="fd864-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="fd864-134">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="fd864-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 <span data-ttu-id="fd864-135">W tym miejscu zmienna typu ciąg jest tworzony z danej wartości, a następnie jego wartość zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="fd864-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="fd864-136">W szczególności, w pierwszym wierszu, wystąpienie typu `String` jest tworzony i podanej wartości `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="fd864-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="fd864-137">W drugim wierszu przykładu, nowe wystąpienie jest tworzony i podanej wartości `Or is it?`, a zmienna string odrzuca odwołanie do pierwszego wystąpienia i przechowuje odwołanie do nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fd864-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="fd864-138">W odróżnieniu od innych typów danych wewnętrznych `String` jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="fd864-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="fd864-139">Jeśli zmienna typu referencyjnego jest przekazywany jako argument do funkcji lub procedury, odwołanie do przechowywania danych adres pamięci jest przekazywany zamiast rzeczywistej wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="fd864-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="fd864-140">W poprzednim przykładzie nazwa zmiennej jest taka sama, ale wskazuje na inną wystąpienie `String` klasy, która zawiera nową wartość.</span><span class="sxs-lookup"><span data-stu-id="fd864-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd864-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd864-141">See Also</span></span>  
 [<span data-ttu-id="fd864-142">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd864-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="fd864-143">String — typ danych</span><span class="sxs-lookup"><span data-stu-id="fd864-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="fd864-144">CHAR — typ danych</span><span class="sxs-lookup"><span data-stu-id="fd864-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="fd864-145">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="fd864-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
