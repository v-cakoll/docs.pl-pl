---
title: Podstawowe informacje o ciągach w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: f1f6b98d7db510373f2729fab2a6e0ad993ea086
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591381"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="3720c-102">Podstawowe informacje o ciągach w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3720c-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="3720c-103">`String` Typ danych reprezentuje szereg znaków (każdy reprezentuje z kolei wystąpienie `Char` — typ danych).</span><span class="sxs-lookup"><span data-stu-id="3720c-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="3720c-104">W tym temacie wprowadzono podstawowe pojęcia ciągów w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3720c-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="3720c-105">Zmienne tekstowe</span><span class="sxs-lookup"><span data-stu-id="3720c-105">String Variables</span></span>  
 <span data-ttu-id="3720c-106">Wystąpienie ciągu można przypisać wartość literału, która reprezentuje serię znaków.</span><span class="sxs-lookup"><span data-stu-id="3720c-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="3720c-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3720c-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="3720c-108">A `String` także zaakceptować wartość zmiennej dowolne wyrażenie zwracające ciąg.</span><span class="sxs-lookup"><span data-stu-id="3720c-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="3720c-109">Odpowiednie przykłady przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="3720c-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="3720c-110">Wszelkie literał, która jest przypisana do `String` zmiennej muszą być ujęte w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="3720c-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="3720c-111">Oznacza to, że znak cudzysłowu w ciągu nie może być przedstawiona przez znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="3720c-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="3720c-112">Na przykład poniższy kod powoduje błąd kompilatora:</span><span class="sxs-lookup"><span data-stu-id="3720c-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="3720c-113">Ten kod powoduje błąd, ponieważ kompilator kończy ciąg po drugim znaku cudzysłowu, a pozostała część ciągu jest interpretowany jako kod.</span><span class="sxs-lookup"><span data-stu-id="3720c-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="3720c-114">Aby rozwiązać ten problem, Visual Basic interpretuje dwa znaki cudzysłowu w ciągu literału jako jeden znak cudzysłowu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="3720c-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="3720c-115">Poniższy przykład przedstawia właściwy sposób, aby uwzględnić znak cudzysłowu w ciągu:</span><span class="sxs-lookup"><span data-stu-id="3720c-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="3720c-116">W poprzednim przykładzie, dwa znaki cudzysłowu poprzedza słowo `Look` stają się jeden znak cudzysłowu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="3720c-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="3720c-117">Trzy znaki cudzysłowu na końcu wiersza reprezentuje jeden znak cudzysłowu w ciągu znaków, a znak zakończenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="3720c-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="3720c-118">Literały ciągu może zawierać wiele wierszy:</span><span class="sxs-lookup"><span data-stu-id="3720c-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="3720c-119">Wynikowy ciąg zawiera sekwencje nowego wiersza, używane w ciągu literału (vbcr, vbcrlf itp.).</span><span class="sxs-lookup"><span data-stu-id="3720c-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="3720c-120">Nie trzeba używać starego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="3720c-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="3720c-121">Znaków w ciągach</span><span class="sxs-lookup"><span data-stu-id="3720c-121">Characters in Strings</span></span>  
 <span data-ttu-id="3720c-122">Ciąg można traktować jako serię `Char` wartości, a `String` typ ma wbudowane funkcje, które umożliwiają wykonywanie wielu manipulacje na ciąg, podobne manipulacje dozwolone przez tablice.</span><span class="sxs-lookup"><span data-stu-id="3720c-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="3720c-123">Podobnie jak wszystkie tablicy w programie .NET Framework są to tablice liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="3720c-123">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="3720c-124">Może odwoływać się do określonego znaku w ciągu za pomocą `Chars` właściwość, która umożliwia dostęp do znaków według położenia, w którym występuje w ciągu.</span><span class="sxs-lookup"><span data-stu-id="3720c-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="3720c-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3720c-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="3720c-126">W powyższym przykładzie `Chars` właściwość ciągu zwraca czwarte znak w ciągu, który jest `D`, a następnie przypisuje go do `myChar`.</span><span class="sxs-lookup"><span data-stu-id="3720c-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="3720c-127">Możesz też pobrać długość określonego ciągu za pomocą `Length` właściwości.</span><span class="sxs-lookup"><span data-stu-id="3720c-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="3720c-128">Jeśli musisz wykonać wiele manipulacje typ tablicy na ciąg można przekonwertować go na tablicę `Char` wystąpień przy użyciu `ToCharArray` funkcja ciągu.</span><span class="sxs-lookup"><span data-stu-id="3720c-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="3720c-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3720c-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="3720c-130">Zmienna `myArray` teraz zawiera tablicę `Char` wartości, reprezentujący znak z `myString`.</span><span class="sxs-lookup"><span data-stu-id="3720c-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="3720c-131">Niezmienność ciągów</span><span class="sxs-lookup"><span data-stu-id="3720c-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="3720c-132">Ciąg jest *niezmienne*, co oznacza, że jego wartość nie można zmienić po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="3720c-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="3720c-133">Jednak to nie uniemożliwiają przypisanie więcej niż jedną wartość do zmiennej ciągu.</span><span class="sxs-lookup"><span data-stu-id="3720c-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="3720c-134">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="3720c-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="3720c-135">W tym miejscu jest tworzony na zmienną ciągu podane wartości, a następnie jego wartość zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="3720c-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="3720c-136">W szczególności w pierwszym wierszu, wystąpienie typu `String` jest tworzona i przypisywana wartość `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="3720c-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="3720c-137">W drugim wierszu przykładu, nowe wystąpienie jest tworzone i podana wartość `Or is it?`, i zmiennej ciągu odrzuca odwołanie do pierwszego wystąpienia i przechowuje odwołania do nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3720c-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="3720c-138">W przeciwieństwie do innych typów danych wewnętrznych `String` jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="3720c-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="3720c-139">Jeśli zmienna typu odwołania jest przekazywany jako argument do funkcji lub podprocedury, odwołanie do adresu pamięci, w którym dane są przechowywane jest przekazywany zamiast rzeczywistej wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="3720c-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="3720c-140">Co w poprzednim przykładzie nazwa zmiennej pozostają takie same, ale wskazuje na nowe i zróżnicowane wystąpienie `String` klasy, która zawiera nową wartość.</span><span class="sxs-lookup"><span data-stu-id="3720c-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3720c-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3720c-141">See also</span></span>

- [<span data-ttu-id="3720c-142">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3720c-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="3720c-143">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="3720c-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="3720c-144">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="3720c-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="3720c-145">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="3720c-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
