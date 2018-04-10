---
title: Niebezpieczny kod i wskaźniki (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32856461fbc6513509342a3567240de723f1fe8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="1650e-102">Niebezpieczny kod i wskaźniki (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1650e-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="1650e-103">Aby zachować bezpieczeństwo typów i zabezpieczeń, C# nie obsługuje arytmetyki wskaźnika domyślnie.</span><span class="sxs-lookup"><span data-stu-id="1650e-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="1650e-104">Jednak przy użyciu [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe, można zdefiniować niebezpiecznym kontekście, w którym można wskaźników.</span><span class="sxs-lookup"><span data-stu-id="1650e-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="1650e-105">Aby uzyskać więcej informacji na temat wskaźników, zobacz temat [typów wskaźnikowych](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="1650e-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1650e-106">W środowisko uruchomieniowe języka wspólnego (CLR) niebezpieczny kod jest określana jako kod niemożliwy do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="1650e-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="1650e-107">Niebezpieczny kod w języku C# nie jest zawsze niebezpieczne; jest tylko kod bezpieczeństwa, którego nie można zweryfikować przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="1650e-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="1650e-108">Środowisko CLR w związku z tym tylko wykona niebezpieczny kod, jeśli jest w pełni zaufanym zestawem.</span><span class="sxs-lookup"><span data-stu-id="1650e-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="1650e-109">Jeśli używasz niebezpieczny kod jest obowiązek upewnij się, że kodu nie wprowadzają zagrożeniem bezpieczeństwa lub wskaźnik błędów.</span><span class="sxs-lookup"><span data-stu-id="1650e-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="1650e-110">Niebezpieczne przegląd kodu</span><span class="sxs-lookup"><span data-stu-id="1650e-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="1650e-111">Niebezpieczny kod ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1650e-111">Unsafe code has the following properties:</span></span>  
  
-   <span data-ttu-id="1650e-112">Metody, typy i bloki kodu mogą być definiowane jako niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="1650e-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
-   <span data-ttu-id="1650e-113">W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji, usuwając kontroli granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="1650e-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
-   <span data-ttu-id="1650e-114">Niebezpieczny kod jest wymagany, gdy wywoływać funkcje natywne, które wymagają wskaźników.</span><span class="sxs-lookup"><span data-stu-id="1650e-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
-   <span data-ttu-id="1650e-115">Przy użyciu niebezpieczny kod wprowadza zagrożenia bezpieczeństwa i stabilności.</span><span class="sxs-lookup"><span data-stu-id="1650e-115">Using unsafe code introduces security and stability risks.</span></span>  
  
-   <span data-ttu-id="1650e-116">Aby C# skompilować kod niezabezpieczony, aplikacja musi być kompilowana przy użyciu [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1650e-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1650e-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1650e-117">Related Sections</span></span>  
 <span data-ttu-id="1650e-118">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="1650e-118">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1650e-119">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="1650e-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [<span data-ttu-id="1650e-120">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="1650e-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [<span data-ttu-id="1650e-121">Porady: użycie wskaźników do kopiowania tablicy bajtów</span><span class="sxs-lookup"><span data-stu-id="1650e-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [<span data-ttu-id="1650e-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="1650e-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="1650e-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1650e-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1650e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1650e-124">See Also</span></span>  
 [<span data-ttu-id="1650e-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1650e-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
