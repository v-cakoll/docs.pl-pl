---
title: 'Instrukcje: wyszukiwanie w ciągu Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700059"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="ef731-102">Instrukcje: wyszukiwanie w ciągu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef731-102">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="ef731-103">W tym artykule przedstawiono przykład sposobu wyszukiwania ciągu w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef731-103">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="ef731-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef731-104">Example</span></span>

<span data-ttu-id="ef731-105">Ten przykład wywołuje metodę <xref:System.String.IndexOf%2A> w obiekcie <xref:System.String>, aby zgłosić indeks pierwszego wystąpienia podciągu:</span><span class="sxs-lookup"><span data-stu-id="ef731-105">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="ef731-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ef731-106">Robust programming</span></span>

<span data-ttu-id="ef731-107">Metoda <xref:System.String.IndexOf%2A> zwraca lokalizację pierwszego znaku pierwszego wystąpienia podciągu.</span><span class="sxs-lookup"><span data-stu-id="ef731-107">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="ef731-108">Indeks jest oparty na 0, co oznacza, że pierwszy znak ciągu ma indeks 0.</span><span class="sxs-lookup"><span data-stu-id="ef731-108">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="ef731-109">Jeśli <xref:System.String.IndexOf%2A> nie odnajdzie podciągu, zwraca-1.</span><span class="sxs-lookup"><span data-stu-id="ef731-109">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="ef731-110">W metodzie <xref:System.String.IndexOf%2A> jest rozróżniana wielkość liter i jest stosowana bieżąca kultura.</span><span class="sxs-lookup"><span data-stu-id="ef731-110">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="ef731-111">Aby zapewnić optymalną kontrolę błędów, możesz chcieć ująć ciąg wyszukiwania w bloku `Try` [try... Catch... Konstrukcja instrukcji finally](../../../language-reference/statements/try-catch-finally-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="ef731-111">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef731-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef731-112">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="ef731-113">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ef731-113">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="ef731-114">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef731-114">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="ef731-115">Ciągi</span><span class="sxs-lookup"><span data-stu-id="ef731-115">Strings</span></span>](index.md)
