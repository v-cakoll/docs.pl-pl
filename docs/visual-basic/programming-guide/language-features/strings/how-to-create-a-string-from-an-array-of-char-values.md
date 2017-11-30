---
title: "Porady: tworzenie ciągu z tablicy wartości znaków (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="50581-102">Porady: tworzenie ciągu z tablicy wartości znaków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50581-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="50581-103">W tym przykładzie tworzy ciągu "abcd" z poszczególnych znaków.</span><span class="sxs-lookup"><span data-stu-id="50581-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50581-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="50581-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="50581-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="50581-105">Compiling the Code</span></span>  
 <span data-ttu-id="50581-106">Ta metoda nie ma specjalnych wymagań.</span><span class="sxs-lookup"><span data-stu-id="50581-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="50581-107">Składnia `"a"c`, w którym jeden `c` następuje jeden znak w znaki cudzysłowu, służy do tworzenia literału znaku.</span><span class="sxs-lookup"><span data-stu-id="50581-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="50581-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="50581-108">Robust Programming</span></span>  
 <span data-ttu-id="50581-109">Znaki null (odpowiednikiem `Chr(0)`) w ciągu dać nieoczekiwane wyniki, korzystając z ciągu.</span><span class="sxs-lookup"><span data-stu-id="50581-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="50581-110">Znak null zostanie uwzględniony w ciągu, ale nie będą wyświetlane po znaku null w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="50581-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50581-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50581-111">See Also</span></span>  
 <xref:System.String>  
 [<span data-ttu-id="50581-112">CHAR — typ danych</span><span class="sxs-lookup"><span data-stu-id="50581-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="50581-113">Typy danych</span><span class="sxs-lookup"><span data-stu-id="50581-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
