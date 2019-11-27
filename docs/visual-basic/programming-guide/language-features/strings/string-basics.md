---
title: Podstawowe informacje o ciągach
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7141966e3c8a8cbce42111c56a85a00709e8fe1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344280"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="f3f64-102">Podstawowe informacje o ciągach w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3f64-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="f3f64-103">Typ danych `String` reprezentuje serię znaków (z których każde reprezentuje wystąpienie typu `Char` danych).</span><span class="sxs-lookup"><span data-stu-id="f3f64-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="f3f64-104">W tym temacie przedstawiono podstawowe pojęcia dotyczące ciągów w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f3f64-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="f3f64-105">Zmienne ciągu</span><span class="sxs-lookup"><span data-stu-id="f3f64-105">String Variables</span></span>  
 <span data-ttu-id="f3f64-106">Do wystąpienia ciągu można przypisać wartość literału, która reprezentuje serię znaków.</span><span class="sxs-lookup"><span data-stu-id="f3f64-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="f3f64-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f3f64-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="f3f64-108">Zmienna `String` może również przyjmować dowolne wyrażenie, które daje w wyniku ciąg.</span><span class="sxs-lookup"><span data-stu-id="f3f64-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="f3f64-109">Odpowiednie przykłady przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="f3f64-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="f3f64-110">Wszystkie literały przypisane do zmiennej `String` muszą być ujęte w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="f3f64-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="f3f64-111">Oznacza to, że znak cudzysłowu w ciągu nie może być reprezentowany przez cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="f3f64-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="f3f64-112">Na przykład następujący kod powoduje błąd kompilatora:</span><span class="sxs-lookup"><span data-stu-id="f3f64-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="f3f64-113">Ten kod powoduje błąd, ponieważ kompilator kończy ciąg po drugim znaku cudzysłowu, a pozostała część tego ciągu jest interpretowana jako kod.</span><span class="sxs-lookup"><span data-stu-id="f3f64-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="f3f64-114">Aby rozwiązać ten problem, Visual Basic interpretuje dwa znaki cudzysłowu w literale ciągu jako jeden znak cudzysłowu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="f3f64-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="f3f64-115">Poniższy przykład ilustruje poprawny sposób dołączania cudzysłowu do ciągu:</span><span class="sxs-lookup"><span data-stu-id="f3f64-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="f3f64-116">W poprzednim przykładzie dwa cudzysłowy poprzedzające wyraz `Look` stają się pojedynczym znakiem cudzysłowu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="f3f64-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="f3f64-117">Trzy cudzysłowy znajdujące się na końcu wiersza reprezentują jeden znak cudzysłowu w ciągu i znak zakończenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="f3f64-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="f3f64-118">Literały ciągu mogą zawierać wiele wierszy:</span><span class="sxs-lookup"><span data-stu-id="f3f64-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="f3f64-119">Ciąg otrzymany zawiera sekwencje nowego wiersza, które były używane w literale ciągu (vbCr, vbCrLf itp.).</span><span class="sxs-lookup"><span data-stu-id="f3f64-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="f3f64-120">Nie trzeba już używać starego obejścia:</span><span class="sxs-lookup"><span data-stu-id="f3f64-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="f3f64-121">Znaki w ciągach</span><span class="sxs-lookup"><span data-stu-id="f3f64-121">Characters in Strings</span></span>  
 <span data-ttu-id="f3f64-122">Ciąg może być uważany za serię wartości `Char`, a typ `String` ma wbudowane funkcje, które umożliwiają wykonywanie wielu operacji w ciągu, który przypomina manipulowanie dozwolone przez tablice.</span><span class="sxs-lookup"><span data-stu-id="f3f64-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="f3f64-123">Podobnie jak w przypadku wszystkich tablic w .NET Framework, są to tablice oparte na zero.</span><span class="sxs-lookup"><span data-stu-id="f3f64-123">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="f3f64-124">Można odwołać się do określonego znaku w ciągu za pomocą właściwości `Chars`, która zapewnia sposób dostępu do znaku przez położenie, w którym występuje w ciągu.</span><span class="sxs-lookup"><span data-stu-id="f3f64-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="f3f64-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f3f64-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="f3f64-126">W powyższym przykładzie właściwość `Chars` ciągu zwraca czwarty znak w ciągu, który jest `D`i przypisuje go do `myChar`.</span><span class="sxs-lookup"><span data-stu-id="f3f64-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="f3f64-127">Możesz również uzyskać długość określonego ciągu za pomocą właściwości `Length`.</span><span class="sxs-lookup"><span data-stu-id="f3f64-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="f3f64-128">Jeśli trzeba wykonać wiele operacji manipulowania typem tablicowym w ciągu, można przekonwertować ją na tablicę wystąpień `Char` przy użyciu funkcji `ToCharArray` ciągu.</span><span class="sxs-lookup"><span data-stu-id="f3f64-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="f3f64-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f3f64-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="f3f64-130">Zmienna `myArray` teraz zawiera tablicę wartości `Char`, z których każdy reprezentuje znak z `myString`.</span><span class="sxs-lookup"><span data-stu-id="f3f64-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="f3f64-131">Niezmienności ciągów</span><span class="sxs-lookup"><span data-stu-id="f3f64-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="f3f64-132">Ciąg jest *niezmienny*, co oznacza, że jego wartość nie może zostać zmieniona po utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="f3f64-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="f3f64-133">Nie uniemożliwia to jednak przypisywania więcej niż jednej wartości do zmiennej ciągu.</span><span class="sxs-lookup"><span data-stu-id="f3f64-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="f3f64-134">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="f3f64-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="f3f64-135">W tym miejscu zostanie utworzona zmienna ciągu, z uwzględnieniem wartości, a następnie jej wartość zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="f3f64-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="f3f64-136">Dokładniej, w pierwszym wierszu zostanie utworzone wystąpienie typu `String` i nadano `This string is immutable`wartość.</span><span class="sxs-lookup"><span data-stu-id="f3f64-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="f3f64-137">W drugim wierszu przykładu zostanie utworzone nowe wystąpienie, pod którym `Or is it?`wartość, a zmienna String odrzuca odwołanie do pierwszego wystąpienia i zapisuje odwołanie do nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f3f64-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="f3f64-138">W przeciwieństwie do innych typów danych wewnętrznych, `String` jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="f3f64-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="f3f64-139">Gdy zmienna typu referencyjnego jest przenoszona jako argument do funkcji lub podprocedury, odwołanie do adresu pamięci, w którym są przechowywane dane jest przekazywane zamiast rzeczywistej wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="f3f64-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="f3f64-140">Dlatego w poprzednim przykładzie nazwa zmiennej pozostaje taka sama, ale wskazuje na nowe i inne wystąpienie klasy `String`, która zawiera nową wartość.</span><span class="sxs-lookup"><span data-stu-id="f3f64-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f64-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3f64-141">See also</span></span>

- [<span data-ttu-id="f3f64-142">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3f64-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="f3f64-143">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="f3f64-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="f3f64-144">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="f3f64-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="f3f64-145">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="f3f64-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
