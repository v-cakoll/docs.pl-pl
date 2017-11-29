---
title: "Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="c2758-102">Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c2758-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>
<span data-ttu-id="c2758-103">W poniższym przykładzie użyto wskaźników do skopiowania do innej tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="c2758-103">The following example uses pointers to copy bytes from one array to another.</span></span>  
  
 <span data-ttu-id="c2758-104">W tym przykładzie użyto [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe, co pozwala na użycie wskaźników w `Copy` metody.</span><span class="sxs-lookup"><span data-stu-id="c2758-104">This example uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="c2758-105">[Stałej](../../../csharp/language-reference/keywords/fixed-statement.md) instrukcji służy do deklarowania wskaźniki do tablic źródłowym i docelowym.</span><span class="sxs-lookup"><span data-stu-id="c2758-105">The [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="c2758-106">To *numerów PIN* lokalizacja źródłowa i docelowa stałych w pamięci, dzięki czemu nie będą przenoszone przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c2758-106">This *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="c2758-107">Bloki pamięci dla tablic są odpiąć, gdy `fixed` bloku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="c2758-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="c2758-108">Ponieważ `Copy` używa metody w tym przykładzie `unsafe` — słowo kluczowe, jego musi być kompilowana przy użyciu **/ unsafe** — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c2758-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the **/unsafe** compiler option.</span></span> <span data-ttu-id="c2758-109">Ustawianie opcji w programie Visual Studio, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c2758-109">To set the option in Visual Studio, right-click the project name, and then click **Properties**.</span></span> <span data-ttu-id="c2758-110">Na **kompilacji** wybierz opcję **niebezpiecznego kodu**.</span><span class="sxs-lookup"><span data-stu-id="c2758-110">On the **Build** tab, select **Allow unsafe code**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2758-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2758-111">Example</span></span>  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c2758-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2758-112">See Also</span></span>  
 [<span data-ttu-id="c2758-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c2758-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c2758-114">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="c2758-114">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="c2758-115">/ unsafe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c2758-115">/unsafe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [<span data-ttu-id="c2758-116">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="c2758-116">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
